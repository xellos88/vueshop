<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <!-- <img alt="Vue logo" src="./assets/iu.jpg"> -->

  <!-- 네비-->
  <Navi :product1="product1" :navList="navList" />
  <!-- <br>
  <input type="text" v-model="inputTest">
  <br>
  <span>{{ inputTest }}</span>
  <br> -->
  <div class="discount" v-if="flg">
    <p>
      지금 당장 구매하시면, {{  timerCount }}%할인
    </p>
  </div><button @click="hookTest = !hookTest">훅테스트</button>
  {{ hookTest }}
  <!-- <div class="startTransition" :class="{endTransition : modalFlg}"> -->
  <Transition name="modalTransition">
    <Modal 
    @closeModal="modalFlg = false;" 
    :products="products" 
    :productNum="productNum" 
    :modalFlg="modalFlg"/>
  </Transition>
  <!-- </div> -->

  <ProductList 
  @openModal="modalFlg = true; productNum = i" 
  :product="product" 
  :productNum="productNum" v-for="(product,i) in products" :key="i"/>
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

  <!-- <div v-for="(item,i) in products" :key="i">
    <img :src="item.img" style="width:300px; height:300px;">
    <h4 @click="openModal(i)">{{ item.name }}</h4>
    <p>{{ item.price }}원</p>
    <span>수량:{{  products[productNum].count }}개</span>
  </div> -->


  
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
      timerCount:100,
      flg:false,
      hookTest:false,
      inputTest:'',
      calinput:'',
      navList:['홈','상품','기타'],
      modalFlg : false,
      products: data,
      product1:'양말',
      price1:'3,800',
      product2:'바지',
      price2:'100,000,000',
      styleR:'color:red',
      productNum:0,
    }
  },
  updated() {
    this.flg=true;
  },
  mounted() {
  // timerCount 변수를 감시(watch)하여 값이 변경될 때마다 실행되는 콜백 함수를 등록합니다.
  this.$watch(
    'timerCount',
      (value) => {
            // 값이 0보다 크면 setTimeout을 사용하여 1초 후에 timerCount를 감소시킵니다.
            if (value > 0) {
              setTimeout(() => {
              this.timerCount--;
            }, 1000);
          }
        },
      { immediate: true } // 즉시 실행 옵션을 설정하여 watch 콜백 함수를 초기 마운트 시에도 실행합니다.
    );
  },
  watch:{ //실시간 감시 함수 정의 영역
    inputTest(input){
      if( input == 3)
      alert('3333');
      this.inputTest='';
    },
  },
  methods: {//함수 설정하는 영역
    plus(i) {
      this.products[i].count++;
      this.productPrice = this.products[i].count * this.products[i].price;
    },
    minus(i) {
      this.products[i].count--;
      this.productPrice = this.products[i].count * this.products[i].price;
    },
    // getImagePath(name) {
    //   return require(`@/assets/${name}.jpg`);
    // },
    // openModal(item) {
    //   this.slt = item;
    //   this.modalFlg = true;
    // },
    openModal(i) {
      this.modalFlg = true;
      this.productNum = i;
      this.productPrice = this.products[i].price;
      this.products[i].count = 1;
    },
    cal(price,count){
      return price * count;
    },
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
