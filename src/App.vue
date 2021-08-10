<template>
<div>
    <div class="black-bg" v-if="모달창열렸니 == true">
      <div class="white-bg">
        <h4>{{원룸들[누른거].title}}</h4>
        <p>{{원룸들[누른거].content}}</p>
        <p>{{원룸들[누른거].price}}원</p>
        <p>상세페이지 내용임</p>
        <button @click="모달창열렸니 = false">닫기</button>
      </div>
    </div>

  
  <!-- <div class="start" :class="{ end : true }" >  -->
   <transition name="fade">
    <Modal @closeModal="모달창열렸니 = false" :원룸들="원룸들" :누른거="누른거"
    :모달창열렸니="모달창열렸니"/>
   </transition>
  <!-- </div> -->

  <div class="menu">
    <a v-for="a in 메뉴들" :key="a">{{a}}</a>
  </div> 

  <Discount v-if="showDiscount == true" />



  <button @click="priceSort">가격순정렬버튼</button>
  <button @click="sortBack">되돌리기</button>
  <Card @openModal="모달창열렸니 = true; 누른거 = $event" :원룸="원룸들
  [i]" v-for="작명 in 원룸들" :key="작명"/>
  <!-- <Card :작명="원룸들[1]"/>
  <Card :작명="원룸들[2]"/>
  <Card :작명="원룸들[3]"/>
  <Card :작명="원룸들[4]"/>
  <Card :작명="원룸들[5]"/> -->


  <div v-for="(a, i) in 원룸들" :key="i">
    <img :src="a.image" class="room-img">
    <h4 @click="모달창열렸니=true; 누른거=i">{{a.title}}</h4>
    <p>{{a.price}}원</p>
  </div>
  
  <!-- <img alt="Vue logo" src="./assets/logo.png">
  <div v-for="(a,i) in products" :key="i"> 
    원룸샵
    <h4> {{a}}원룸 </h4>
    <p> 50만원 </p>
    <button @click="increase">허위매물신고</button>\
    <span>신고수 : {{신고수}}</span>
    </div> -->
   <!-- <div> 
    <img src="./assets/room0.jpg" class="room-img">
    <h4 @click="모달창열렸니 =true"> {{products[0]}}원룸 </h4>
    <p> 70만원 </p>
    <button @click="신고수[0]++"> 허위매물신고</button>
    <span>신고수 : {{신고수[0]}}</span>
  </div>
  <div> 
    <img src="./assets/room1.jpg" class="room-img">
    <h4> {{products[1]}}원룸 </h4>
    <p> 70만원 </p>
    <button @click="신고수[1]++">허위매물신고</button>
    <span>신고수 : {{신고수[1]}}</span>
  </div>
  <div> 
    <img src="./assets/room2.jpg" class="room-img">
    <h4> {{products[2]}}원룸 </h4>
    <p> 70만원 </p>
    <button @click="신고수[2]++">허위매물신고</button>
    <span>신고수 : {{신고수[2]}}</span>
  </div> -->
</div>
</template>



<script>

import data from './assets/oneroom.js';
import Discount from './Discount.vue';
import Modal from './Modal.vue';
import Card from './Card.vue';


export default {
  name: 'App',
  data(){
    return {
      showDiscount : true,
      원룸들오리지널 : [...data],
      오브젝트 : {name : 'kim', age : 20 },
      누른거 : 0,
      원룸들 : data,
      모달창열렸니 : true,
      신고수 : [0,0,0],
      메뉴들 : ['Home','Shop','About'],
      products : ['역삼동원룸','천호동원룸','마포구원룸'],
    }
  },
  methods : {
    increase(){
      this.신고수 +=1;
    },

    sortBack(){
      this.원룸들 = [...this.원룸들오리지널];

    },
    priceSort(){
      this.원룸들.sort(function(a,b){
        return a.price - b.price
      });
    },
  },

  created(){


  },

  mounted(){
    setTimeout(()=>{
      this.showDiscount = false;
    }, 2000);
  },


  
  components: {
    Discount : Discount,
    Modal : Modal,
    Card : Card,
  }
}
</script>



<style>
.fade-leave-from {
  opacity:1;
}
.fade-leave-active {
  transition: all 1s;
}
.fade-leave-to {
  opacity:0;
}



.fade-enter-from {
  transform: translateY(-1000px);
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  transform:translateY(0px);
}

body{
  margin : 0
}
div{
  box-sizing: border-box;
}
.discount{
  background: #eee;
  padding: 10px;
  margin : 10px;
  border-radius : 5px;
}
.black-bg {
  width:100%; height:100%;
  background: rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
}
.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding :20px;
}

.room-img{
  width: 100%;
  margin-top: 40px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.menu{
  background : darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a{
  color : white;
  padding : 10px;
}
</style>
