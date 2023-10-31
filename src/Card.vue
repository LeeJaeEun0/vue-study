<template>
  <img :src="a.image" class="room-img" />
    <h4
      @click=" send"
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
    },
    methods:{
        send(){
            this.$emit('openModal', this.a.id)
        }
    }
}
</script>

<style>

</style>