<template>
  <div id="app">
    <header>
      <h1>Vue.js SPA</h1>
    </header>
    <main>
      <aside class="sidebar">
        <ol>
          <li v-for="post in posts" :key="post.id">
            {{ post.title }}
          </li>
        </ol>
      </aside>
      <div class="content">
      </div>
    </main>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      posts: null,
      endpoint: "https://jsonplaceholder.typicode.com/posts/"
    };
  },
  created() {
    this.getAllPost();
  },
  methods: {
    getAllPost() {
      axios
        .get(this.endpoint)
        .then(response => {
          this.posts = response.data;
        })
        .catch(error => {
          console.log("----Error----");
          console.error(error);
        });
    }
  }
};
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 20px;
}
header {
  border-bottom: 1px solid gray;
  position: sticky;
  top: 0;
  background-color: white;
  padding: 20px 0;
}
main {
  display: flex;
}
.sidebar {
  width: 30%;
  border-right: 1px solid gray;
  padding: 10px 20px;
  text-align: left;
}
.content {
  width: 70%;
}

h1,
h2 {
  font-weight: normal;
  margin: 0;
}
li {
  margin: 10px 0;
}
a {
  color: #42b983;
}
</style>
