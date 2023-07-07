<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <!-- <img alt="Vue logo" src="./assets/iu.jpg"> -->

  <!-- 네비-->
  <Navi :product1="product1" :navList="navList" />
  <!-- <div class="nav">
      <a>홈</a>
      <a>상품</a>
      <a>기타</a>
  </div> -->


  <!-- <div v-for="(item,i) in products" :key="i">
    <img alt="Vue logo" src="./assets/티셔츠.jpg">
    <img :src="item.img" style="width:300px; height:300px;">
    <img :src="getImagePath(item.name)" style="width:200px; height:200px;">
    <h4 @click="openModal(item)" :class="{ aa: slt === item }">{{ item.name }}</h4>
    <p>{{ item.price }}원</p>
    <button @click="plus(i)">+</button>
    <button @click="minus(i)">-</button>
    <span>{{ item.count }}</span>
  </div> -->
  <!-- <div class="bg_black" v-if="modalFlg">
    <div class="bg_white" style="width:500px; height:500px;">
      <img :src="products[productNum].img " style="width: 300px; height: 300px;">
        <h4>상품명: {{ products[productNum].name }}</h4>
        <p>설명: {{ products[productNum].content  }}</p>
        <span>수량:{{  products[productNum].count }}개</span>
        <button @click="plus(productNum)">+</button>
        <button @click="minus(productNum)">-</button>
        <p>가격: {{ cal(products[productNum].price, products[productNum].count) }}</p>
        <button @click="modalFlg = false">닫기</button>
    </div>
  </div> -->
  <ProductList @openModal="modalFlg = true;" :product="product" v-for="(product,i) in products" :key="i"/>
  <!-- <div v-for="(item,i) in products" :key="i">
    <img :src="item.img" style="width:300px; height:300px;">
    <h4 @click="openModal(i)">{{ item.name }}</h4>
    <p>{{ item.price }}원</p>
    <span>수량:{{  products[productNum].count }}개</span>
  </div> -->
  <Modal @closeModal="modalFlg = false" :modalFlg="modalFlg" :products="products" :productNum="productNum"/>

  
  <!-- if -->
  <p v-if="1==1">if문 테스트</p>

  <!-- <div>
    <h4>{{ product1 }}</h4>
    <p>{{ price1 }}원</p>
  </div>
  <div>
    <h4 :style='styleR'>{{ product2 }}</h4>
    <p>{{ price2 }}원</p>
  </div> -->

</template>

<script>
import data from './assets/js/data.js';
import Navi from './components/Navi.vue';
import ProductList from './components/ProductList.vue';
import Modal from './components/Modal.vue';

export default {
  name: 'App',
  data(){//데이터 바인딩
    return{
      // products:[
      //   {name:'티셔츠',price:'10000',count:1},
      //   {name:'바지',price:'20000',count:1},
      //   {name:'점퍼',price:'30000',count:1},
      // ],
      navList:['홈','상품','기타'],
      modalFlg : false,
      products: data,
      product1:'양말',
      price1:'3,800',
      product2:'바지',
      price2:'100,000,000',
      styleR:'color:red',
      productNum:0,
      // slt: null,
    }
  },
  methods: {//함수 설정하는 영역
    plus(i){
      this.products[i].count++;
    },
    minus(i){
      this.products[i].count--;
    },
    // getImagePath(name) {
    //   return require(`@/assets/${name}.jpg`);
    // },
    // openModal(item) {
    //   this.slt = item;
    //   this.modalFlg = true;
    // },
    openModal(i) {
      this.productNum = i;
      this.modalFlg = true;
    },
    cal(price,count){
      return price * count;
    }
  },
  components: { //컴포넌트 정의
    Navi,
    ProductList,
    Modal,
  },
}
</script>

<style>
@import url('./assets/css/app.css');

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
