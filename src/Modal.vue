<template>
     <div class="black-bg" v-if="모달창 == true"><!-- 1==1은 참일 경우, 1==2는 거짓, 참일때 보임-->
    <div class="white-bg">
      <img :src="원룸들[clickNumber].image" class="room-img">
      <h4>{{원룸들[clickNumber].title}}</h4>
      <p>{{원룸들[clickNumber].price}}</p>
      <p>{{원룸들[clickNumber].content}}</p>
      <button @click="$emit('closeModal')"> 닫기</button>
    <!-- 자식은 모달창 = false 처럼 변경 불가능 -->
    </div>
  </div>
</template>

<script>
export default {
    //eslint-disable-next-line
    name : "Modal",
    props : {
        // 변수명 : 타입
        원룸들 : Object,
        clickNumber : Number,
        모달창 : Boolean
    }

}
</script>

<style>

</style>