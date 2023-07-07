<template>
    <div class="bg_black" v-if="modalFlg">
        <div class="bg_white" style="width:500px; height:500px;">
            <img :src="products[productNum].img" style="width:300px; height:300px;">
            <h4>{{ products[productNum].name }}</h4>
            <p>{{ products[productNum].content }}</p>
            <p> {{ products[productNum].price }}</p>
            <!-- <button @click="$emit('plus(productNum)')">증가</button>
            <button  @click="$emit('minus(productNum)')">감소</button> -->
            <!-- <span>수량:{{  $emit(products[productNum].count) }}개</span> -->
            <br>
            <button @click="$emit('closeModal');">닫기</button>
        </div>
    </div>
</template>
<script>
export default {
    name: 'Modal',
    props: {
        modalFlg: Boolean,
        products: Object,
        productNum: Number,
    },
};
</script>

<style>
    
</style>