<template>
  <!-- <p v-for="(item, i) in foods" :key="i">{{ item }}</p> -->
  <div class="modal" v-if="isModal">
    <div class="inner">
      <h3>{{ data[selectedMovie].title }}</h3>
      <p>영화 상세정보</p>
      <!-- props로 전달받은 데이터는 부모만 변경 가능 -->
      <!-- 부모에게 이벤트를 전달, 요청할 수 있음 emit 함수를 통해 전달 -->
      <!-- $emit('이벤트명') -->
      <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>
  export default {
    name: "ModalComponent",
    props: {
      data: Array,
      isModal: Boolean,
      selectedMovie: Number,
    }
  }
</script>

<style>

</style>