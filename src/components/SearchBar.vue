<template>
  <div class="search-box">
    <!-- @input="inputText = $event.target.value" -->
    <!-- v-model="변수" 사용자에게 입력받은 값을 변수에 알아서 저장 -->
    <!-- v-model="inputText" -->
    <input
        type="search"
        @change="
          $emit('searchMovie', $event.target.value)
          inputText = $event.target.value;
          $event.target.value = ''
        "
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
    },
    props: {
      data: Array,
    },
    // 검색창에 사용자 값이 올바른지 검사
    // watch 데이터 안에 특정 데이터가 변경될때마다 실행되는 코드
    watch: { // 특정 상태변수가 변경됨을 감지하는 hook
    // 동작하는 조건: 데이터가 남아있으면 안되고 변경되야 함
    // 검사할 변수명(변경값, 이전값) { 로직 }
    // inputText 변수가 검사대상
      inputText(name) {
        // 입력한 영화제목이 데이터에 있는지 확인
        const findName = this.data.filter(movie => {
          return movie.title.includes(name);
        })
        if(findName.length === 0) {
          alert('해당하는 자료가 없습니다.');
        }
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