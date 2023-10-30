<template>
  <div class="menu"> 
      <a v-for="i in menu" :key="i">{{i}}</a>
    </div>

  <div  v-for="i in products" :key="i" > 
    <h4 :style="스타일">{{i}}</h4>
    <p>100 만원</p>
  </div>


</template>
<script>


export default {
  name: 'App',
  data(){
    return {
      스타일: "color:blue",
      menu : ['Home', 'Shop', 'About'],
      products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
    }
  },
  components: {
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.menu{
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a{
  color: white;
  padding: 10px;
}
</style>
