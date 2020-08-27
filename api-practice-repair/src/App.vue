<template>
  <div id="app">
    <h1>API情報</h1>
    <!-- <div
      v-for="post in posts"
      :key="post.id"
    >
      <br>
      テーブル Start
      <div class="data">
        <table>
          <tbody>
            id表示
            <tr class="data-id">
              {{post.id}}
            </tr>
            title表示
            <tr class="data-title">
              {{post.title}}
            </tr>
            completed表示、trueなら完了、falseは未完了
            <tr class="data-completed" v-if='post.completed'>
              完了
            </tr>
            <tr class="data-completed" v-else>
              未完了
            </tr>
          </tbody>
        </table>
      </div>
      テーブル End
    </div> -->
    <ul class="data-lists">
      <li v-for="post in posts" :key="post.id" class="data">
        <span class="data-id">{{ post.id }}</span>
        <h3 class="data-title">{{ post.title }}</h3>
        <span class="data-completed" v-if="post.completed">完了</span>
        <span class="data-completed data-completed-no" v-else>未完了</span>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';

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
    });
  },
};
</script>

<style lang="scss">
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    max-width: 800px;
    margin: 0 auto;
    // margin: 60px 0 100px 0;
    // position: absolute;
    // left: 50%;
    // transform: translate(-50%);
    // -ms-transform: translate(-50%);
    // -webkit-transform: translate(-50%);
    // width: 800px;
    // .data {
    //     margin-bottom: 10px;
    //     tbody {
    //         display: flex;
    //     }
    //     &-id {
    //         position: absolute;
    //             left: 0px;
    //     }
    //     &-title {
    //         padding-left: 50px;
    //         position: absolute;
    //             left: 50%;
    //         transform: translate(-50%);
    //             -ms-transform: translate(-50%);
    //             -webkit-transform: translate(-50%);
    //         width: 700px;
    //     }
    //     &-completed {
    //         position: absolute;
    //             right: 0px;
    //     }
    // }
}

.data-lists{
  list-style: none;
  padding: 0;
}

.data {
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
  justify-content: space-between;
  padding: 10px 0;
  border-top: 1px solid #eeeeee;

  @media screen and (min-width:769px) {
    flex-direction: row;
    padding: 20px 0;
  }

  &-id {
    font-weight: bold;
    display: block;
  }

  &-completed {
    font-weight: bold;
    display: block;
    margin-top: 15px;
    color: skyblue;

    @media screen and (min-width:769px) {
      margin-top: 0;
  }

    &-no {
      color: red;
    }
  }

  &-title {
    margin: 0;
  }
}

</style>
