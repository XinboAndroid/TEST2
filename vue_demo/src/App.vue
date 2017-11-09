<template>
  <div id="app">
    <!--<img src="./assets/logo.png">-->
    <!--<router-view></router-view>-->
    <ul>
      <input type="text" v-on:keyup.enter="bindEnter(msg)" v-model="msg" placeholder="Add a todo">
      <li v-for="todo in todos" v-bind:class="{finish:todo.isFinish}"
          v-text="todo.text"
          v-on:click="toggleFinish(todo)">
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'app',
  data: () => {
      return {
        msg: 'aaa',
        todos:[
          {
            text:'学习vue',
            isFinish: true
          },
          {
            text:'学习node',
            isFinish: true
          },
          {
            text:'学习reactnative',
            isFinish: false
          }
        ]
      }
  },
  methods:{
    bindEnter:function (msg) {
      console.log(msg)
      this.msg = ''
      this.todos.push({
        text:msg,
        isFinish: false
      })
    },
    toggleFinish:function(todo){
      console.log(todo)
      todo.isFinish = !todo.isFinish
    }
  },

  watch:{
    msg: function (newVal, oldVal) {
      console.log('新: '+ newVal)
      console.log(`旧${oldVal}`)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin: 60px 60px;
}

  .finish{
    text-decoration: line-through;
  }
</style>
