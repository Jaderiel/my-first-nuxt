<template>
    <div v-if="product">
        <p>{{ product.title }}</p>
        <p>{{ product.price }}</p>
        <p>{{ product.id }}</p>
    </div>
    <div v-else>
        <p>Loading...</p>
    </div>
</template>

<script setup>
    import { useRoute } from '@nuxtjs/composition-api';

    const { id } = useRoute().params
    const uri = 'https://fakestoreapi.com/products' + id;

    //fetch the product
    const {data: product} =await useFetch(uri);
    
    definePageMeta ({
        layout: 'products'
    })
</script>

<style scoped>
    h2 {
        margin-bottom: 20px;
        font-size: 36px;
    }
    p {
        margin: 20px 0;
    }
</style>