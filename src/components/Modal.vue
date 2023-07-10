<template>
    <div class="bg_black" v-if="modalFlg">
        <div class="bg_white" style="width:500px; height:500px;">
            <img :src="products[productNum].img" style="width:300px; height:300px;">
            <h4>상품:{{ products[productNum].name }}</h4>
            <p>설명:{{ products[productNum].content }}</p>
        <!-- <button @click="$emit('plus')">증가</button>
            <button  @click="$emit('minus')">감소</button>-->
            <p>가격:{{ inputCnt * products[productNum].price }}</p>
            <span>수량:</span>
            <input type="number" v-model="inputCnt">
            <button @click="$emit('closeModal'); inputCnt=0;">닫기</button>
        </div>
    </div>
</template>
<script>
export default {
    name: 'Modal',
    data(){
        return{
            inputCnt:0,
        }

    },
    props: {
        modalFlg: Boolean,
        products: Object,
        productNum: Number,
    },
    watch: {
    inputCnt(Val) {
        if (Val > 10) {
        alert('10개까지만 구매 가능합니다.');
        this.inputCnt = 10;
        }
    }
    }
};
</script>
<style>

</style>