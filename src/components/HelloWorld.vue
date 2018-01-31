<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Essential Links</h2>
    <ul>
      <li>
        <a
          href="https://vuejs.org"
          target="_blank"
        >
          Core Docs
        </a>
      </li>
      <li>
        <a
          href="https://forum.vuejs.org"
          target="_blank"
        >
          Forum
        </a>
      </li>
      <li>
        <a
          href="https://chat.vuejs.org"
          target="_blank"
        >
          Community Chat
        </a>
      </li>
      <li>
        <a
          href="https://twitter.com/vuejs"
          target="_blank"
        >
          Twitter
        </a>
      </li>
      <br>
      <li>
        <a
          href="http://vuejs-templates.github.io/webpack/"
          target="_blank"
        >
          Docs for This Template
        </a>
      </li>
    </ul>
    <h2>Ecosystem</h2>
    <ul>
      <li>
        <a
          href="http://router.vuejs.org/"
          target="_blank"
        >
          vue-router
        </a>
      </li>
      <li>
        <a
          href="http://vuex.vuejs.org/"
          target="_blank"
        >
          vuex
        </a>
      </li>
      <li>
        <a
          href="http://vue-loader.vuejs.org/"
          target="_blank"
        >
          vue-loader
        </a>
      </li>
      <li>
        <a
          href="https://github.com/vuejs/awesome-vue"
          target="_blank"
        >
          awesome-vue
        </a>
      </li>
    </ul>

    <!--<ul v-if="posts && posts.length">-->
     <li v-for="post of posts">
       <p><strong>{{post.title}}</strong></p>
       <p>{{post.body}}</p>
     </li>
    <!--</ul>

    <ul v-if="errors && errors.length"> -->
      <li v-for="error of errors">
        {{error.message}}
      </li>
    <!--</ul>-->

    <input type="text" v-model="postBody" @change="postPost()"/>
    <!--<ul v-if="errors && errors.length"> -->
      <li v-for="error of errors">
        {{error.message}}
      </li>
    <!--</ul> -->
  </div>

    <ul>
      <li v-for="todo in todos" v-bind:key='todo.id'>
         {{ todo.id }} => {{ todo.label }}
      </li>
    </ul>
</template>

<script>
  import axios from 'axios';

export default {
  name: 'HelloWorld',

  data() {
      return {
        msg: 'Todo list',
        postBody: '',
        todos: []
      }
    },

    created() {
      axios.get('http://localhost:8000/api/todos')
      .then(response => {
        // JSON responses are automatically parsed.
        this.todos = response.data
      })
      .catch(e => {
        //this.errors.push(e)
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
