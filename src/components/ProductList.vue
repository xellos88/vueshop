<template>
    <div>
        <img :src="product.img" alt="" style="width:400px; height:400px;" >
        <h4 @click="$emit('openModal');">{{ product.name }}</h4>
        <p>{{ product.price }}원</p>
        <p>{{ product.count }}개</p>
    </div>
</template>

<script>
export default {
    name: 'ProductList',
    props: {
        product: Object,
        productNum: Number,
        // { name: '티셔츠', content: '셔츠셔츠셔츠', price: '10000', count: 1, img: require('@/assets/티셔츠.jpg') },가 오브젝트라서
    }  
}
</script>
<style>
</style>