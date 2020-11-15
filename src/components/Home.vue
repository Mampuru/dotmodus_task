<template>
  <div class="columns medium-3" v-for="result in Articles" :key="result.id">
  <div class="card">
    <div class="card-divider">
      {{ result.title }}
    </div>
    <div class="card-section">
      <p>{{ result.publishedAt }}.</p>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: 'home',
  data() {
    return {
      Articles: [],
    };
  },
methods: {
    fetchPosts() {
      fetch("http://newsapi.org/v2/top-headlines?country=us&apiKey=")
        .then(response => response.json())
        .then(data => (this.Articles = data.articles));
        console.log(this.Articles.title)
    }
  },
 mounted() {
    this.fetchPosts();
  }
}
</script>


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
