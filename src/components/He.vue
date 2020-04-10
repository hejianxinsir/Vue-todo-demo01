<template>
  <div class="todo-list-example">
    <!-- form 表单 v-on:submit.prevent="xxx"
      label--添加todo，for 属性要绑定 input 的 id 值
      imput--输入框 用 v-model 双向绑定 newTodoText 数据，默认为空字符串
      button--添加按钮

    ul--包裹li
      li v-for="item in items"；data 里自定义 items 数组；{{item.title}};
      li 还有个 删除按钮--v-on:click="yyy" 这个yyy删除方法就是把数组的这一项去掉
    -->
    <form v-on:submit.prevent="xxx" class="form-title">
      <label for="ooo">Add an item</label>
      <input type="text" id="ooo"
        placeholder="add here..."
        v-model="newTodoText"
      >
      <button>add</button>
    </form>

    <ul>
      <li v-for="(item,index) in items" :key="item.id"> 
        {{item.title}}
        <button @click="items.splice(index,1)">done</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'todoListTest',
  data(){
    return {
      newTodoText: '',
      newTodoTextId: 4,
      items: [
        {id: 1, title: '飞韩国看演唱会'},
        {id: 2, title: '去日本游山玩水'},
        {id: 3, title: '可以回来加班了'}
      ]
    }
  },
  methods: {
    yyy(){
      // 完成按钮，删除数组的对应项
      this.items.splice(index,1)
    },
    xxx(){
      // 添加事项
      this.items.push({id: this.newTodoTextId, title: this.newTodoText})
      this.newTodoTextId += 1
      this.newTodoText = ''
    }
  } 
}
</script>


<style scoped>
.todo-list-example{
  border: 3px solid lightgray;
  border-radius: 5px;
  padding: 20px 0;
  min-width: 30%;
  font-size: 16px;
}
.todo-list-example ul{
  list-style: none;
}
.form-title{
  color: brown;
}
.form-title input{
  color: brown;
  outline: none;
  border: 1px solid gray;
  border-radius: 3px;
  margin: 0 10px;
  padding: 4px 7px;
}
.todo-list-example>ul>li>button,
.form-title > button{
  color: brown;
  border: 1px solid lightgray;
  border-radius: 3px;
  padding: 4px 7px;
  font-size: 14px;
}
.todo-list-example>ul>li>button{
  position: absolute;
  right: 10px;
}

.todo-list-example ul{
  margin: 20px 0;
  max-width: 70%;
  margin-left: 35px;
}
.todo-list-example ul li{
  margin-bottom: 15px;
  position: relative;
  padding: 5px 0;
}
</style>