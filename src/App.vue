<template>

  <nav>
    <a v-for="(item, idx) in menu" :key="idx" href="#">{{item}}</a>
  </nav>

  
  <div class="view" v-for="(item, idx) in info" :key="idx">
    <h4 @click="모달볼래=true; num = idx">{{info[idx].원룸지역}} 원룸</h4>
    <p>{{info[idx].price}}만원</p>
    <button @click="increment(item)">신고</button> <span>신고건수 : {{info[idx].신고}}</span>
  </div>

  

  <div v-if="모달볼래==true">
    <div class="modal">
      <div class="modal-base">
        <h2>{{info[num].원룸지역}}원룸</h2>
        <p>{{info[num].price}} 만원</p>
        <p>{{info[num].설명}}</p>
        <button @click="모달볼래=false">닫기</button>
      </div>
    </div>
  </div>
  

</template>

<script>

import room from './roomData.js';




export default {
  
  name: 'App',
  data(){
    return{
      모달볼래: false,
      menu: ['홈', '물건찾기', '계약하기'],
      info: room,
      num: 0
    }
  },
  components: { },
  methods:{
    increment(self){
      self.신고++;
    }
  }
}

</script>

<style>
*{box-sizing: border-box; margin:0; padding:0;}
ul, li, ol{list-style: none;}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
p{
  color: #f00;
}
nav{
  padding: 20px;
  background-color: darkblue;
}
nav a{
  font-size: 18px;
  color: #fff;
  text-decoration: none;
  padding: 0 20px;
}
.modal{
  position: fixed;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.3);
  display: flex;
  justify-content: center;
  align-items: center;
}
.modal-base{
  padding: 20px;
  background-color: #fff;
  border-radius: 10px;
  
}
.modal-base>p{
  color: #000;
}

</style>
