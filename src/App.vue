<template>

  <div class="black-bg" v-if="open_modal">
    <div class="white-bg">
      <h4 style="font-size: 30px;">{{modal_title}}</h4>
      <img :src="modal_image" class="room-img">
      <p>{{modal_content}}</p>
      <p>가격 : {{modal_price}}</p>
      <button @click="open_modal=false">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a href="#" v-for="(item, i) in menu" :key="(item,i)">{{item}}</a>
  </div>


  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <div v-for="(item, i) in oneroom" :key="(item, i)">
    <img :src="item.image" class="room-img">
    <h4 @click="fnc_openModal(i)">{{item.title}}</h4>
    <p>{{item.price}}</p>
    <button @click="increase(i)">허위매물신고</button> <span>신고수 : {{item.report}}</span>
  </div>
</template>

<script>
// import {apple, apple2} from './assets/oneroom.js';
import data from './assets/oneroom.js';
data


export default {
  name: 'App',
  data(){
    return{
      open_modal : false,
      menu : ['Home', 'Shop', 'About'],
      products : [
        {
          h4: '역삼동원룸',
          price : '50만원',
          report : 0
        }, 
        {
          h4 : '천호동원룸',
          price : '40만원',
          report : 0
        }, 
        {
          h4 : '마포구원룸',
          price : '20만원',
          report : 0
        }
      ],
      oneroom: data,
      modal_title : '',
      modal_image : '',
      modal_content : '',
      modal_price : 0,
    }
  },
  methods : {
    increase(i){
      console.log(i)
      this.oneroom[i].report++;
    },
    fnc_openModal(i){
      this.open_modal = true
      console.log(i)
      this.modal_title = this.oneroom[i].title
      this.modal_image = this.oneroom[i].image
      this.modal_content = this.oneroom[i].content
      this.modal_price = this.oneroom[i].price
    }
  },
  components: {
  }
}
</script>

<style>
body {
  margin: 0
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

.room-img {
  width: 100%;
  margin-top: 40px;
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
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}
</style>
