<template>
  <div v-if="1 == 2">안녕하세요</div>
  <div v-else-if="1 == 3">안녕하세요2</div>
  <div v-else>안녕하세요3</div>

<!-- <div class="start" :class="{end : 모달창}">
  <Modal @closeModal="모달창=false" :원룸들="원룸들" :모달창="모달창" :clickNumber="clickNumber"/>
</div> -->

<transition name="fade">
  <Modal @closeModal="모달창=false" :원룸들="원룸들" :모달창="모달창" :clickNumber="clickNumber"/>
</transition>

  <div class="menu">
    <a v-for="i in menu" :key="i">{{ i }}</a>
  </div>

  <Discount v-bind="오브젝트" :이름="오브젝트.이름"/>

  <button @click="priceSort">가격순 정렬 버튼</button>
  <button @click="priceSortDesc">가격역순 정렬 버튼</button>
  <button @click="nameeSort">이름순 정렬 버튼</button>
  <button @click="sortBack">되돌아기 버튼 버튼</button>

  <!-- <div  v-for="(a,i) in products" :key="i" > 
    <h4>{{products[i]}}</h4>
    <h4>{{a}}</h4>
    <p>100 만원</p>
  </div> -->

  <!-- <div>
    <img src="./assets/room0.jpg" class="room-img" />
    <h4 @click="모달창 = true">{{ products[0] }}</h4>
    <p>100 만원</p>
    <button @click="신고수[0]++">허위매물신고</button>
    <span>신고수 : {{ 신고수[0] }}</span> -->
    <!-- <button @click="신고수++" >허위매물신고</button> <span>신고수 : {{신고수}}</span> -->
    <!-- <button  @mouseover="신고수++">허위매물신고</button> <span>신고수 : {{신고수}}</span> -->
    <!-- <button v-on:click="">허위매물신고</button> <span>신고수 : 0</span> -->
  <!-- </div>
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
  </div> -->

  <!-- <div> 
  <img :src="원룸들[0].image" class="room-img">
    <h4>{{원룸들[0].title}}</h4>
    <p>{{원룸들[0].price}}</p>
  </div>
  <div>  -->
<!-- 
  <div v-for="(a, i) in 원룸들" :key="i">
    <Card :a="a" :i="i"/>
  </div> -->
  <div >
    <Card @openModal="모달창=true;clickNumber=$event" :a="원룸들[i]" v-for="(a, i) in 원룸들" :key="i"/>
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
      원룸들오리지널 : [...data], // array, object 별개의 사본을 만들기 위함
      // data로 하면 sort로 변형 되기 때문
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
    priceSort(){
      // var array = [3,4,2];
      // array.sort() // 문자 정렬
      // sort는 원본데이터를 변경 , map, filter는 원본을 변형하지 않음
      this.원룸들.sort(function(a,b){ // 숫자 정렬인 경우
        return a.price - b.price // 양수면 왼쪽에 b, 음수면 a가 왼쪽에 가도록 함
      });

    },
    priceSortDesc(){
      this.원룸들.sort()
      // this.원룸들.sort(function(a,b){ // 숫자 정렬인 경우
      //   return b.price - a.price // 양수면 왼쪽에 b, 음수면 a가 왼쪽에 가도록 함
      // });

    },
    nameSort(){
      this.원룸들.sort(function(a,b){ 
        return a.title.localeCompare(b.title)
      });

    },
    sortBack(){
      // 등호는 왼쪽 오른쪽 값을 공유해달라는 의미
      // this.원룸들 = this.원룸들오리지널;
      this.원룸들 = [...this.원룸들오리지널];
    }
  },
  components: {
    Discount: Discount, // Discount로 축약가능
    Modal: Modal,
    Card: Card,
  },
};
</script>

<style>
/* -enter-는 등장, -leace-는 퇴장 */


.fade-enter-from{
  /* 시작 */
  transform: translateY(-1000px);
} 
.fade-enter-active{
  /* transition */
  transition: all 1s;
}
.fade-enter-to{
  /* 끝 */
  transform: translateY(0px);
}

.fade-leave-from{
  /* 시작 */
  opacity: 1;
} 
.fade-leave-active{
  /* transition */
  transition: all 1s;
}
.fade-leave-to{
  /* 끝 */
  opacity: 0;
}

.start{
  opacity: 0;
  transition: all 1s;
}
.end{
  opacity: 1;
}
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
