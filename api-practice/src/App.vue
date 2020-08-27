<template>
  <div id="app">
    <h1>API情報</h1>
    <div
      v-for="post in posts"
      :key="post.id"
    >
      <br>
      <!-- テーブル Start -->
      <div class="data">
        <table>
          <tbody>
            <!-- id表示 -->
            <tr class="data-id">
              {{post.id}}
            </tr>
            <!-- title表示 -->
            <tr class="data-title">
              {{post.title}}
            </tr>
            <!-- completed表示、trueなら完了、falseは未完了 -->
            <tr class="data-completed" v-if='post.completed === true'>
              完了
            </tr>
            <tr class="data-completed" v-else>
              未完了
            </tr>
          </tbody>
        </table>
      </div>
      <!-- テーブル End -->
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
