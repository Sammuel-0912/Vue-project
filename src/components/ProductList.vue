<template>
        <div class="col-md-8">
            <h2 class="mb-3">商品列表</h2>
            <div class="row">
                <div v-for="product in products" :key="product.id" class="col-md-4 mb-4">
                    <div class="card h-100">
                        <img :src="product.image">
                        <div class="card-body">
                        <h5 class="card-title">{{ product.name }}</h5>
                        <p class="card-text">{{ product.description }}</p>
                        <p class="fw-bold text-primary">{{ product.price }}</p>
                        <button class="btn btn-success w-100" @click="handleAddCart(product)"> 加入購物車 </button>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
</template>

<script setup>
import { defineProps } from 'vue';
import { inject } from 'vue'; 

const props = defineProps({
    products: {
        type: Array,
        required: true,
    }
}) 
const emit = defineEmits(["add-Cart"])

const handleAddCart = (product)  => {
    emit("add-Cart",product)
    showNotification(`商品 ${product.name} 已加入購物車`)
}

const showNotification = inject('showNotification')

</script>
