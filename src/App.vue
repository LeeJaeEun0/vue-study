<template>
  <div v-if="1 == 2">안녕하세요</div>
  <div v-else-if="1 == 3">안녕하세요2</div>
  <div v-else>안녕하세요3</div>

  <Modal :원룸들="원룸들" :모달창="모달창" :clickNumber="clickNumber"/>

  <div class="menu">
    <a v-for="i in menu" :key="i">{{ i }}</a>
  </div>

  <Discount />

  <!-- <div  v-for="(a,i) in products" :key="i" > 
    <h4>{{products[i]}}</h4>
    <h4>{{a}}</h4>
    <p>100 만원</p>
  </div> -->

  <div>
    <img src="./assets/room0.jpg" class="room-img" />
    <h4 @click="모달창 = true">{{ products[0] }}</h4>
    <p>100 만원</p>
    <button @click="신고수[0]++">허위매물신고</button>
    <span>신고수 : {{ 신고수[0] }}</span>
    <!-- <button @click="신고수++" >허위매물신고</button> <span>신고수 : {{신고수}}</span> -->
    <!-- <button  @mouseover="신고수++">허위매물신고</button> <span>신고수 : {{신고수}}</span> -->
    <!-- <button v-on:click="">허위매물신고</button> <span>신고수 : 0</span> -->
  </div>
  <div>
    <img src="./assets/room1.jpg" class="room-img" />
    <h4 @click="모달창 = true">{{ products[1] }}</h4>
    <p>70 만원</p>
    <button @click="신고수[1]++">허위매물신고</button>
    <span>신고수 : {{ 신고수[1] }}</span>
  </div>
  <div>
    <img src="./assets/room2.jpg" class="room-img" />
    <h4 @click="모달창 = true">{{ products[2] }}</h4>
    <p>90 만원</p>
    <button @click="신고수[2]++">허위매물신고</button>
    <span>신고수 : {{ 신고수[2] }}</span>
  </div>

  <!-- <div> 
  <img :src="원룸들[0].image" class="room-img">
    <h4>{{원룸들[0].title}}</h4>
    <p>{{원룸들[0].price}}</p>
  </div>
  <div>  -->

  <div v-for="(a, i) in 원룸들" :key="i">
    <Card :a="a" :i="i"/>
  </div>

</template>
<script>
import data from "./assets/data.js";
import Discount from "./Discount.vue";
import Modal from "./Modal.vue";
import Card from "./Card.vue";
export default {
  name: "App",
  data() {
    return {
      오브젝트 : {name:'kim', age : 20},
      clickNumber: 0,
      원룸들: data,
      신고수: [0, 0, 0],
      menu: ["Home", "Shop", "About"],
      products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
      모달창: false,
    };
  },
  methods: {
    increase(i) {
      this.신고수[i] += 1;
    },
  },
  components: {
    Discount: Discount, // Discount로 축약가능
    Modal: Modal,
    Card: Card,
  },
};
</script>

<style>
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}

.room-img {
  width: 100%;
  margin-top: 40px;
}
</style>
