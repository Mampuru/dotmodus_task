<template>
 <div class="card"  v-for="result in Articles" :key="result.id">
     <h1 id="header"> {{ result.title }}</h1>
     <p class="description">{{ result.description }}</p>
     <p id="publisher"> {{ result.source.name }} : {{ result.publishedAt }}</p>
  </div>
  <br/>
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
.card {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  max-width: 50%;
  margin: auto;
  border-radius: 30px;
  font-family: arial;
}

.description {
  color: grey;
  font-size: 22px;
  padding: 1%;
}

#header{
  padding: 2%;
}

#publisher{
  text-align: end;
  padding: 0% 3% 1% 0%;
}
</style>
