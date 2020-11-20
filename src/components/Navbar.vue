<template>
    <ul class="topnav">
        <li><a class="active" href="#home">Home</a></li>
        <li class="right"><a href="#contact">Contact</a></li>
        <li class="right"><a href="#about">About</a></li>
    </ul>
</template>

<script>
export default {
  data() {
    return {
    };
  },
}
</script>


<style scoped>
ul.topnav {
  list-style-type: none;
  margin: 0;
  padding: 0;
  overflow: hidden;
  background-color: #333;
}

ul.topnav li {float: left;}

ul.topnav li a {
  display: block;
  color: white;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
}

ul.topnav li a:hover:not(.active) {background-color: #111;}

ul.topnav li a.active {background-color: #4c8baf;}

ul.topnav li.right {float: right;}

@media screen and (max-width: 600px) {
  ul.topnav li.right, 
  ul.topnav li {float: none;}
}
</style>
