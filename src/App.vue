<template>
<!--  데이터 바인딩 : html 안에 데이터를 넣는것-->
<h1>영화정보</h1>
<div v-for="(movie, i) in data" :key="i">
<!-- 데이터를 표시할 때 중괄호 두개 -->
<!-- 속성에 값을 바인딩할 때 앞에 콜론(:)을 붙여주면 됨 :속성명="데이터" -->
  <h3 class="bg-yellow" :style="textRed">{{ movie.title }}</h3>
  <p>개봉: {{ movie.year }}</p>
  <p>장르: {{ movie.category }}</p>
  <!-- v-on:이벤트명="실행코드, v-on 축약식: @로 대체 가능 -->
  <!-- 코드가 짧을 경우 바로 추가 -->
  <!-- <button @:click="like++">좋아요</button> <span>{{ like }}</span> -->
  <!-- 버튼을 눌렀을 때 인덱스 값을 전달해야 함 -->
  <button @:click="increaseLike(i)">좋아요</button> <span>{{ movie.like }}</span>
</div>
  <!-- 반복문(배열의 자료명, 인덱스) -->
  <!-- <p v-for="(item, i) in foods" :key="i">{{ item }}</p> -->
</template>


<script> // 문서에 보여질 데이터를 작성할 때 script 안에 작성
export default { // 안에 기능 정의
  name: 'App', // 컴포넌트명
  data() {  // 문서에 표시될 상태 변수
    return { // return 안에 변수 정의
      data: [
        {
          title: "노랑",
          year: 2023,
          category: "액션, 드라마",
          textRed: "color: red",
          like: 0,
        },
        {
          title: "아쿠아맨과 로스트 킹덤",
          year: 2023,
          category: "액션, 판타지, 어드벤처",
          textRed: "color: red",
          like: 0,
        },
        {
          title: "아쿠아맨과 로스트 킹덤",
          year: 2023,
          category: "액션, 판타지, 어드벤처",
          textRed: "color: red",
          like: 0,
        },
      ]
    }
  },
  methods: { // 함수 추가 가능
    increaseLike(i) {
      // 객체 안에 있는 like 변수를 찾아야 , 객체 내부에서 사용하는 변수는 앞에 this를 붙여야 함
      this.data[i].like += 1
    }
  }
}
</script>

<style>
  .bg-yellow {
    background: gold;
    padding: 10px;
  }
</style>
