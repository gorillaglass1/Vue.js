<template>
  <img class="vue" alt="Vue logo" src="./assets/logo.png">

  <div class="black-bg" v-if="alert == true">
    <div class="white-bg">
      <h4>안내 사항</h4>
      <p>부동산 <span style="color: red;">사기에</span> 주의하십시오.</p>
      <button @click="alert = false">닫기</button>
    </div>
  </div>

  <div class="black-bg" v-if="Inquirealert == true">
    <div class="white-bg">
      <h4>문의</h4>
      <p>해당 부동산의 판매자를 
        <span style="color: red;">찾을 수 없습니다.</span></p>
      <button @click="Inquirealert = false">닫기</button>
    </div>
  </div>

  <div class="black-bg" v-if="reportsub == true">
    <div class="white-bg">
      <h4>신고접수</h4>
      <p>신고당한 내용을 적어주세요.</p>
      <p><input type="text" name="report"> <br>
      <input type="submit" name="sent">&nbsp;</p>
      <button @click="reportsub = false">취소</button>
    </div>
  </div>


  <div class="menu">
    <a class="menu">뷰동산</a><br><br>
    <a v-for="(a, i) in menu" :key="i">
    {{ a }}
    </a>
  </div>

  <div v-for="(a, i) in source" :key="i">
    <hr>
    <img class="roomimage" :src = 'a.image'>
    <h4>원룸: {{ a.title }}</h4>
    <p>특징: {{ a.content }}</p>
    <p>가격: {{ a.price }}원 </p>
    <p>
      <button @click="Inquirealert = true">문의하기</button>
    </p>
    <p>신고횟수: {{ report[i] }}회 <button @click="increase(i)">신고하기</button></p>
    <p><button @click="reportsub = true">신고 접수하기</button></p>
  </div>
  
</template>

<script>

import oneroomdata from './assets/oneroom.js';

export default {
  name: 'App',
  data() {
    return{
      source : oneroomdata,
      alert : true,
      Inquirealert : false,
      report : [0, 0, 0, 0, 0, 0],
      reportsub : false,
      menu : ['Home', 'Shop', 'About'],
    }
  },
  methods: {
    increase(num) {
      this.report[num]++ ;
    }
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
  margin-top: 60px;
}

.vue {
  width: 50px;
  height: 50px;
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
