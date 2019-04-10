<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <input v-model="keyword" placeholder="検索キーワードを入力">
    <button @click="searchMovies">検索</button>

    <table class="table" v-show="results">
      <tr>
        <th>#</th>
        <th>ムービー</th>
        <th>情報</th>
      </tr>
      <tr v-for="(movie, index) in results" v-bind:key="movie.id.videoId">
        <td>{{ index + 1 }}</td>
        <td>
          <a v-bind:href="'https://www.youtube.com/watch?v=' + movie.id.videoId">
            <img width="320" height="180" v-bind:src="movie.snippet.thumbnails.medium.url">
          </a>
        </td>
        <td>
          <b>{{ movie.snippet.title }}</b>
          <br>
          <span class="desc">
            {{
            movie.snippet.description
            }}
          </span>
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
import axios from 'axios';
import 'bootstrap/dist/css/bootstrap.min.css';

export default {
  name: "SearchYoutube",
  data: function() {
    return {
      results: null,
      keyword: "Giulietta Machine",
      params: {
        q: "", // 検索文字列
        part: "snippet",
        type: "video",
        maxResults: "10", // 最大検索数
        key: "AIzaSyDtPV43IJnQeVA64qCb8hJ7MIRr7k2DgrE"
      }
    };
  },
  props: {
    msg: String
  },
  methods: {
    searchMovies: function() {
      this.params.q = this.keyword;
      var self = this;
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: this.params
        })
        .then(function(res) {
          self.results = res.data.items;
        })
    }
  }
};
</script>

<style scoped>
.desc {
  color: gray;
}
</style>
