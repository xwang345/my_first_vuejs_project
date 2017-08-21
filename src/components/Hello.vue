<template>
  <div class="hello">
    <h1>{{title}}</h1>
    <!-- <h1 v-html='title'></h1>  -->
    <!-- The alternative way to wirte <h1 v-text="title"></h1> -->
    <!-- The both works -->
    <ul>
      <li v-for="item in items">{{item.label}}</li>
    </ul>
  </div>
</template>

<script>
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
      ]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
