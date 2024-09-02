<template>
  <div class="search-box">
    <!-- @input="inputText = $event.target.value" -->
    <!-- v-model="변수" 사용자에게 입력받은 값을 변수에 알아서 저장-->
    <input
        type="search"
        v-model="inputText"
        placeholder="검색어 입력"
    >
    <button>검색</button>
  </div>
  <p>{{ inputText }}</p>
</template>

<script>
  export default {
    name: "SearchBarComponent",
    data() {
      return {
        inputText: '',
      }
    }
  }
</script>

<style>
  .search-box {
    padding: 10px;
    display: flex;
    justify-content: center;
  }

  .search-box input {
    padding: 5px 10px;
  }

  .search-box button {
    margin: 0;
  }
</style>