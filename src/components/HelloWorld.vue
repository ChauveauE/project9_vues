<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <ul>
      <li v-for="todo in todos" v-bind:key='todo.id'>
         {{ todo.id }} => {{ todo.label }}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'HelloWorld',

  data () {
    return {
      msg: 'Todo list',
      postBody: '',
      todos: []
    }
  },

  created () {
    axios.get('http://localhost:8000/api/todos')
      .then(response => {
        // JSON responses are automatically parsed.
        this.todos = response.data
      })
      .catch(e => {
        // this.errors.push(e)
        console.log(e)
      })
  }

  // Pushes posts to the server when called.
//      postPost() {
//      axios.post(`http://jsonplaceholder.typicode.com/posts`, {
//        body: this.postBody
//      })
//      .then(response => {})
//      .catch(e => {
//        this.errors.push(e)
//      })

//    }
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
