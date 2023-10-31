<template>
  <img :src="a.image" class="room-img" />
    <h4
      @click="
        모달창 = true;
        clickNumber = i;
      "
    >
      {{ a.title }}
    </h4>
    <p>{{ a.price }}</p>
</template>

<script>
export default {
    //eslint-disable-next-line
    name : 'Card',
    props : {
        // 변수명 : 타입
        a:Object,
        i:Number
    }
}
</script>

<style>

</style>