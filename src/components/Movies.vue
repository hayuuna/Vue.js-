<template>
  <div class="container">
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
        <button @:click="$emit('increaseLike', i)">좋아요</button>
        <span>{{ movie.like }}</span>
        <p>
          <button
              @click="$emit('openModal', i)">상세보기</button>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "MoviesComponent",
    props: {
      data: Array,
    }
  }
</script>

<style>
  .container {
    padding: 20px;
  }
</style>