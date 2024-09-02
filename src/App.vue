<template>
  <!--  데이터 바인딩 : html 안에 데이터를 넣는것-->
  <Navbar />
  <!-- 속성명(props 변수="보낼 값" -->
  <Event :text="text"/>
  <h1>영화정보</h1>
  <!-- 반복문(배열의 자료명, 인덱스) -->
  <div v-for="(movie, i) in data" :key="i" class="item">
    <figure>
      <img :src="`${movie.imgUrl}`" :alt="movie.title">
    </figure>
    <div class="info">
    <!-- 데이터를 표시할 때 중괄호 두개 -->
    <!-- 속성에 값을 바인딩할 때 앞에 콜론(:)을 붙여주면 됨 :속성명="데이터" -->
      <h3 class="bg-yellow" :style="textRed">{{ movie.title }}</h3>
      <p>개봉: {{ movie.year }}</p>
      <p>장르: {{ movie.category }}</p>
      <!-- v-on:이벤트명="실행코드, v-on 축약식: @로 대체 가능 -->
      <!-- 코드가 짧을 경우 바로 추가 -->
      <!-- <button @:click="like++">좋아요</button> <span>{{ like }}</span> -->
      <!-- 버튼을 눌렀을 때 인덱스 값을 전달해야 함 -->
      <button @:click="increaseLike(i)">좋아요</button>
      <span>{{ movie.like }}</span>
      <p>
        <button @click="isModal=true; selectedMovie=i">상세보기</button>
      </p>
    </div>
  </div>
<!--  <Modal />-->
</template>


<script> // 문서에 보여질 데이터를 작성할 때 script 안에 작성
// import { 가져올 변수명1, 변수명2 } from '경로' 가져오는 변수가 하나일 때
// import 가져올 변수명 from '경로' 가져오는 변수가 하나일 때
import data from './assets/movies';
import Navbar from "./components/Navbar.vue";
// import Modal from "./components/Modal.vue";
import Event from "./components/Event.vue"; //이벤트 박스
console.log(data);

export default { // 안에 기능 정의
  name: 'App', // 컴포넌트명
  data() {  // 문서에 표시될 상태 변수
    return { // return 안에 변수 정의
      isModal: false,
      data: data,
      selectedMovie: 0,
      text: "NEPLIX 강렬한 운명의 드라마!!!"
    }
  },
  methods: { // 함수 추가 가능
    increaseLike(i) {
      // 객체 안에 있는 like 변수를 찾아야 , 객체 내부에서 사용하는 변수는 앞에 this를 붙여야 함
      this.data[i].like += 1
    }
  },
  components: {
    // 변수명: import로 불러온 컴포넌트명(같은 이름으로 하는것이 관례)
    Navbar: Navbar,
    // Modal: Modal,
    Event: Event,
  }
}
</script>

<style>
  * {
    box-sizing: border-box;
    margin: 0;
  }

  body {
    max-width: 768px;
    margin: 0 auto;
    padding: 20px;
  }

  h1,
  h2,
  h3 {
    margin-bottom: 1rem;
  }

  p {
    margin-bottom: 0.5rem;
  }

  button {
    margin-right: 10px;
    margin-top: 1rem;
  }

  .item {
    width: 100%;
    border: 1px solid #ccc;
    display: flex;
    margin-bottom: 20px;
    padding: 1rem;
  }

  .item figure {
    width: 30%;
    margin-right: 1rem;
  }

  .item img {
    width: 100%;
  }

  .item .info {
    width: 100%;
  }

  .modal {
    background: rgba(0, 0, 0, 0.7);
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .modal .inner {
    background: #fff;
    width: 80%;
    padding: 20px;
    border-radius: 10px;
  }
</style>
