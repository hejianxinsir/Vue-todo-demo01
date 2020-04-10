<template>
  <div class="wrapper">
    <p style="white-space: pre-line">{{message}}</p>
    <textarea v-model="message" id="" cols="30" rows="10"></textarea>
    <hr>
    
    <!-- 单个复选框绑定到布尔值 -->
    走路 <input type="checkbox" id="checkbox" v-model="checked">
    <label for="checkbox">{{checked}}</label>
    <hr>

    <!-- 多个复选框绑定到同一个数组 -->
    <input type="checkbox" id="jack" value="jack" v-model="arr1">
    <label for="jack">jack</label>
    <input type="checkbox" id="xinxin" value="xinxin" v-model="arr1">
    <label for="xinxin">xinxin</label>
    <input type="checkbox" id="hehe" value="hehe" v-model="arr1">
    <label for="hehe">hehe</label>
    <p>已选：{{arr1}}</p>

    <!-- 单选按钮 -->
    <input type="radio" id="hk" value="hongkong" v-model="picked">
    <label for="hk">hongkong</label>
    <input type="radio" id="ou" value="xiangggg" v-model="picked">
    <label for="ou">xiangggg</label>
    <hr>

    <!-- 选择框--单选 -->
    <select v-model="selected">
      <option disabled value="">请选择</option>
      <option>a</option>
      <option>b</option>
      <option>c</option>
    </select>
    <p>{{selected}}</p>
    <hr>

    <!-- 选择框--多选 -->
    <select v-model="multiArr" multiple style="width: 50px;">
      <option value="" disabled>请选择</option>
      <option>A</option>
      <option>B</option>
      <option>C</option>
    </select>
    <p>selected: {{multiArr}}</p>
    <hr>

    <!-- 单个插槽的用法 -->
    <comp1 title="我是title">
      <p>我是父组件的内容</p>
    </comp1>

    <!-- 具名插槽 slot="xxx"  name="xxx"-->
    <comp2>
      <p slot="header">我是第一段--header</p>
      <p slot="main">我是第二段</p>
      <p slot="footer">我是第三段</p>
    </comp2>
    <hr>

    <!-- 作用域插槽: 父组件通过 slot 从子组件拿到数据 -->
    <comp3>
      <!-- 2.5.0 是这种写法 -->
      <template slot="abc" slot-scope="prop">  <!-- 必须使用template, 在template中写slot-scope-->
        {{prop.text}}
        {{prop.xxx}}
      </template>

      <!-- 2.5.0 之后是这种写法, 也就是说不用 template 了！-->
      <p slot="ccc" slot-scope="prop">
        {{prop.text}}
      </p>
    </comp3>

    <!-- 访问 slot this.$slot.name-->
    <comp4>
      <div slot="nnn" slot-scope="prop">
        {{prop.text}}
        <p slot="lll">我是ppppp</p>
      </div>
    </comp4>

    <!-- 动态组件 -->





  </div>
</template>


<script>
export default {
  name: 'test',
  props: ['ttt'],
  data(){
    return {
      message: '111',
      checked: true,
      arr1: [],
      picked: '',
      selected: '',
      multiArr: []
    }
  },
  methods: {

  },
  components: {
    'comp1': {
      template: '<p class="child1">\
        <slot>如果父组件没有插入内容，我作为默认内容显示</slot>\
      </p>',
      props: ['title']
    },
    'comp2': {
      template: `<div class="caomp2">
        <div class="header">
          <slot name="header"></slot>
        </div>
        <slot name="main"></slot>
        <slot name="footer"></slot>
      </div>`
    },
    'comp3': {
      template: `<div>
        <slot text="我是来自子组件的数据" name="abc"  xxx="我是子组件的xxx"></slot>
        <slot text="我是第二个slot的内容" name="ccc"></slot>
        <slot name="lll"></slot>
      </div>
      `
    },
    'comp4': {
      template: `<div>
        <div class="header">
          <slot name="nnn" text="我是comp4"></slot>
        </div>
      </div>`,
      mounted(){
        console.log('com4 mounted')
        console.log(this)
        var info = this.$slots.lll
        console.log(info)
      }
    }
  }
}
</script>

<style scoped>
.wrapper{
  border: 3px solid lightgray;
  width: 100%;
  min-height: 300px;
}
</style>