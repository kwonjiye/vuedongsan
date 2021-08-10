<template>
  <div>
  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <p>{{원룸들[누른거].image}}</p>
      <h4>{{원룸들[누른거].title}}</h4>
      <p>{{원룸들[누른거].content}}</p>
      <textarea v-model.number="month" ></textarea>
      <input type="range" id ="hello" min="1" max="12">
      <!-- <select v-model="month" >
        <option>1</option>
        <option>2</option>
        <option>3</option>
        <option>4</option>
        <option>5</option>
        <option>6</option>
        <option>7</option>
        <option>8</option>
        <option>9</option>
        <option>10</option>
        <option>11</option>
        <option>12</option>

      </select>
       -->
    
      <p>{{month}}개월선택함 : {{원룸들[누른거].price + month}}원</p>
      <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
  </div>
</template>

<script>
export default {
    name:'Modal',
    data(){
      return {
        month : 1, //숫자가 들어옵니다.
        date : 123,
        type : ''
      }

    },
    watch : {
      month(a){
        if(a>=13){
          alert('13이상 입력하지 마셈')
        }
        else if(a==2){
          <p>2개월은 안해요</p>
      
            
        }
      }
    },
  //   watch : {
  //     month(a){
  //       if(a==2){
  //       alert('2개월은 안해요')
  //     }
  //   }
  // },
    props :{
        원룸들 : Array,
        누른거 : Number,
        모달창열렸니 : Boolean,
    }

}
</script>

<style>

</style>