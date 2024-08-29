<template>
<!--  데이터 바인딩 : html 안에 데이터를 넣는것-->
<h1>영화정보</h1>
<div v-for="(movie, i) in data" :key="i">
<!-- 데이터를 표시할 때 중괄호 두개 -->
<!-- 속성에 값을 바인딩할 때 앞에 콜론(:)을 붙여주면 됨 :속성명="데이터" -->
  <h3 class="bg-yellow" :style="textRed">{{ movie.title }}</h3>
  <p>개봉: {{ movie.year }}</p>
  <p>장르: {{ movie.category }}</p>
</div>
  <!-- 반복문(배열의 자료명, 인덱스) -->
  <!--  <p v-for="(item, i) in foods" :key="i">{{ item }}</p>-->
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
          textRed: "color: red"
        },
        {
          title: "아쿠아맨과 로스트 킹덤",
          year: 2023,
          category: "액션, 판타지, 어드벤처",
          textRed: "color: red"
        },
        {
          title: "아쿠아맨과 로스트 킹덤",
          year: 2023,
          category: "액션, 판타지, 어드벤처",
          textRed: "color: red"
        },
      ]
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
