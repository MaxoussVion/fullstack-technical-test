<template>
  <div class="movies">
    <table>
      <thead>
      <tr>
        <th @click="sort('rank')">Rank</th>
        <th @click="sort('title')">Title</th>
        <th @click="sort('synopsis')">Synopsis</th>
        <th @click="sort('director')">Director</th>
        <th @click="sort('duration')">Duration</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="movie in moviesList">
        <td v-for="(value, index) in movie" v-if="index != 'id'">{{ value }}</td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
  export default {
    name: 'MoviesList',
    props: {
      moviesList: Array,
    },
    data() {
      return {
        columns: ["rank", "title", "synopsis", "director", "duration"],
        sortAsc: true,
        isActive: ""
      }
    },
    methods: {
      sort:function(sortInput) {
        if(sortInput === this.currentSort) {
          this.currentSortDir = this.currentSortDir==='asc'?'desc':'asc';
        }
        this.currentSort = sortInput;
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
