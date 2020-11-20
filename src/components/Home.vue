<template>
<div>
  <input placeholder="Search" type="text" @input="input" :value='value'/>
</div>
 <div class="card"  v-for="result in Articles" :key="result.id">
     <h1 id="header"> {{ result.title }}</h1>
     <img :src="result.urlToImage"/>
     <p class="description">{{ result.description }}</p>
     <p id="publisher"> {{ result.source.name }} : {{ result.publishedAt }}</p>
  </div>
</template>

<script>
const api = "http://newsapi.org/v2/top-headlines?country=us&apiKey=";

export default {
  data() {
    return {
      Articles: [],
      value: ''
    };
  },
methods: {
    input($event){
      this.value = $event.target.value
      if(this.value.length == 3){
          fetch('http://newsapi.org/v2/everything?q='+this.value+'&from=2020-11-13&sortBy=popularity&apiKey=', {
        mode: 'cors'
        })
        .then(response => response.json())
        .then(data => (this.Articles = data.articles));
      }
    },
    fetchPosts() {
      fetch(api, {
        mode: 'cors'
        })
        .then(response => response.json())
        .then(data => (this.Articles = data.articles));
    }
  },
 mounted() {
      this.fetchPosts();
  },
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

img{
 width: 100%; 
}

#header{
  padding: 2%;
}

#publisher{
  text-align: end;
  padding: 0% 3% 1% 0%;
}

input[type=text] {
  width: 50%;
  box-sizing: border-box;
  border: 2px solid #ccc;
  border-radius: 10px;
  font-size: 16px;
  background-color: white;
  background-position: 10px 10px; 
  background-repeat: no-repeat;
  padding: 12px 20px 12px 40px;
}
</style>
