<template>
  <div id="app">
    <h1>API情報</h1>
    <div
      v-for="post in posts"
      :key="post.id"
    >
      <br>
      <div class="data">
        <table>
          <tbody>
            <tr class="data-id">
              {{post.id}}
            </tr>
            <tr class="data-title">
              {{post.title}}
            </tr>
            <tr class="data-completed" v-if='post.completed === true'>
              完了
            </tr>
            <tr class="data-completed" v-else>
              未完了
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>import axios from './axios-auth';

export default {
  data() {
    return {
      posts: []
    };
  },
  created() {
    axios
    .get('https://jsonplaceholder.typicode.com/todos')
    .then(response => {
      this.posts = response.data;
      // console.log(response.data)
    });
  },
};
</script>

<style>
@import './sass/index.css'
</style>
