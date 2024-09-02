<template>
  <!--  데이터 바인딩 : html 안에 데이터를 넣는것-->
  <Navbar />
  <!-- 속성명(props 변수="보낼 값" -->
  <Event :text="text"/>
  <SearchBar
      :data="data_temp"
      @searchMovie="searchMovie($event)"
  />
  <p>
    <button @click="showAllMovie">전체보기</button>
  </p>
  <Movies
      :data="data_temp"
      @openModal="isModal=true;selectedMovie=$event"
      @increaseLike="increaseLike($event)"
  />
  <!-- closeModal이벤트를 전달받아 상태 변경 -->
  <Modal
      :data="data"
      :isModal="isModal"
      :selectedMovie="selectedMovie"
      @closeModal="isModal=false"
  />
</template>

<script> // 문서에 보여질 데이터를 작성할 때 script 안에 작성
// import { 가져올 변수명1, 변수명2 } from '경로' 가져오는 변수가 하나일 때
// import 가져올 변수명 from '경로' 가져오는 변수가 하나일 때
import data from './assets/movies';
import Navbar from "./components/Navbar.vue";
import Modal from "./components/Modal.vue";
import Event from "./components/Event.vue"; //이벤트 박스
import Movies from "./components/Movies.vue";
import SearchBar from "./components/SearchBar.vue";

export default { // 안에 기능 정의
  name: 'App', // 컴포넌트명
  data() {  // 문서에 표시될 상태 변수
    return { // return 안에 변수 정의
      isModal: false,
      data: data, // 원본
      data_temp: [...data], // 사본
      selectedMovie: 0,
      text: "NEPLIX 강렬한 운명의 드라마!!!"
    }
  },
  methods: { // 함수 추가 가능
    increaseLike(id) {
      // 객체 안에 있는 like 변수를 찾아야 , 객체 내부에서 사용하는 변수는 앞에 this를 붙여야 함
      this.data.find(movie => {
        if(movie.id === id) {
          movie.like += 1;
        }
      })
    },
    searchMovie(title) {
      // 영화 제목이 포함된 데이터를 가져옴
      this.data_temp = this.data.filter(movie => {
        return movie.title.includes(title);
      })
    },
    showAllMovie() {
      this.data_temp = [...this.data]
    }
  },
  components: {
    // 변수명: import로 불러온 컴포넌트명(같은 이름으로 하는것이 관례)
    Navbar: Navbar,
    Modal: Modal,
    Event: Event,
    Movies: Movies,
    SearchBar: SearchBar,
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
