<template>
  <div class="hello">
      <button @click="randomGen()">Click Me!</button><br /><br />
      <div v-if="this.info === true">
        <h3>Title: {{this.title}}</h3>
        <p>Released in {{this.date}}</p>
        <p>{{this.overview}}</p>
        <a :href="imdbUrl" target="_blank">Find your movie on IMDb</a>
      </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'RandomGenerator',
  data () {
    return {
      randomNumber: 0,
      info: false,
      title: '',
      date: '',
      overview: '',
      imdbUrl: '',
      apiKey: 'a36c05d13fe5bdb40ecdfa5e559a6fff'
    }
  },
  methods: {
    pad (num, len) {
      var str = '' + num
      while (str.length < len) {
        str = '0' + str
      }
      return str
    },
    randomGen () {
      this.randomNumber = this.pad(Math.floor((Math.random() * 2155529) + 1), 8)
      axios
        .get(`http://api.themoviedb.org/3/movie/${this.randomNumber}?api_key=${this.apiKey}`)
        .then((response) => {
          console.log(response.data)
          this.title = response.data.title
          this.date = response.data.release_date.substring(0, 4)
          this.overview = response.data.overview
          this.imdbUrl = 'https://imdb.com/title/' + response.data.imdb_id
          this.info = true
        })
        .catch(() => {
          this.info = false
          this.randomGen()
        })
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
