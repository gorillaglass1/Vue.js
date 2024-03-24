<template>

  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>상세페이지 내용임</p>
      <botton @click="모달창열렸니 = false">닫기</botton>
    </div>
  </div>

  <div class="menu">
    <a v-for="작명 in 메뉴들" :key="작명">{{작명}}</a> <!--작명 부분이 array 안 element가 들어가고 array element 갯수만큼 반복됨, key의 역할 반복문 돌린 요소를 구분-->
  </div>

  <div>
    <img class="roomImage" :src="원룸들[0].image">
    <h4 @click="모달창열렸니 = true">{{  원룸들[0].title }}</h4>
    <p>{{ 원룸들[0].price }}원</p>
    <button @click="increase(0)">허위매물신고</button> <span>신고수 : {{ 신고수[0] }}</span>
  </div>
  <div>
    <img class="roomImage" src="./assets/room1.jpg">
    <h4>{{ products[1] }}</h4>
    <p>70만원</p>
    <button @click="increase(1)">허위매물신고</button> <span>신고수 : {{ 신고수[1] }}</span>
  </div>
    <div>
    <img class="roomImage" src="./assets/room2.jpg">
    <h4>{{ products[2] }}</h4>
    <p>80만원</p>
    <button @click="increase(2)">허위매물신고</button> <span>신고수 : {{ 신고수[2] }}</span>
  </div>

  <!-- <div>
    <h4>{{ products[0] }}</h4>
    <p>60만원</p>
    <button @click="신고수[0]++">허위매물신고</button> <span>신고수 : {{ 신고수[0] }}</span>
  </div>
  <div>
    <h4>{{ products[1] }}</h4>
    <p>70만원</p>
    <button @click="신고수[1]++">허위매물신고</button> <span>신고수 : {{ 신고수[1] }}</span>
  </div>
    <div>
    <h4>{{ products[2] }}</h4>
    <p>80만원</p>
    <button @click="신고수[2]++">허위매물신고</button> <span>신고수 : {{ 신고수[2] }}</span>
  </div> -->
</template>

<script>
  

import data from './assets/oneroom.js';

//import {apple, apple2} from './assets/oneroom.js'; //apple은 마음대로 작명가능;
//apple;
//apple2;


export default {
  name: 'App',
  data(){
    return{
      //데이터 보관함
      원룸들 : data,
      모달창열렸니 : false,
      신고수 : [0,0,0],
      메뉴들 : ['Home', 'Shop', 'About'],
      products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
    }
  },
  methods : {
    increase(num) {
      this.신고수[num]++ ;
    },
  },
  components: {
  }
}
</script>

<style>
body {
  margin : 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%; height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed; padding: 20px;
}
.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}



#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-block: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}
.roomImage {
  width: 100;
  margin-top: 40px;
}
</style>
