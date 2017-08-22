<template>
  <div class="app">
    <!-- <h1>{{title}}</h1> -->
    <h1 v-html='title'></h1>
    <input v-model="newItem" v-on:keyup.enter="addNew">
    <!-- The alternative way to wirte <h1 v-text="title"></h1> -->
    <!-- The both works -->
    <ul>
      <li v-for="item in items" v-bind:class="{finished: item.isFinished}" v-on:click="toggleFinish(item)">
        {{item.lable}}
      </li>
    </ul>
    <component-a msgfromparent='This mssage from parent!!!'></component-a>
  </div>
</template>

<script>
import Store from './store.js'
import ComponentA from './components/componentA.vue'
console.log(ComponentA);
export default {
  data () { //the alternative way data: function (){}
    return {
      title: '<span>???</span>This is a todo list',
      // msg: 'Welcome to Your Vue.js App',
      // msg2: 'Hello to Vue world'
      // now I use <h1 v-text="title"></h1> to decleare a <span> tag in the HTML see what happened?
      // title: ' <span>???</span>This is a todo list'
      // The anwser is the <h1 v-text="title"></h1> do not escape the <span> tag, and will display "<span>???</span>This is a todo list" in the browser
      // So, to solve this problem we use <h1 v-html='title'></h1> to declear it
      // Now, we want to make the todo list
      items: [
        {
          lable: 'todo coding',
          isFinished: false
        },
        {
          lable: 'eating',
          isFinished: true
        }
      ],
      liClass: 'this is liClass',
        }
      },
      components: { ComponentA },
      watch: {
        items:{
            handler: function (items) {
                Store.save(items);
            },
            deep: true
        }
      },
      methods: {
        toggleFinish: (item) => {
          item.isFinished = !item.isFinished;
    },
    addNew: function() {
      this.items.push({
        lable: this.newItem,
        isFinished: false
      })
      this.newItem = '';
    }
  }
}
</script>

<style>
.finished {
  text-decoration: underline;
}
component-a {
  color: red;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
