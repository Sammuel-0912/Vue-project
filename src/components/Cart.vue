<template>
    <div class="col-md-4">
      <h2 class="mb-3">購物車</h2>
      <div v-if="carts.length === 0">購物車是空的</div>
      <ul class="list-group mb-3">
        <li v-for="item in carts" :key="item.id" class="list-group-item d-flex justify-content-between align-items-center">
          <div>
            <h6 class="my-0">{{ item.name }}</h6>
            <small class="text-muted">{{ item.quantity }}</small>
          </div>
          <div>
            <span class="text-muted">{{ item.quantity * item.price }}</span>
            <button class="btn btn-sm btn-outline-danger ms-2" @click="handleRemoveCart(item)"> 移除 </button>
          </div>
        </li>
      </ul>
    </div>

</template>

<script setup>

import { inject } from 'vue'; 


const props = defineProps({
    carts: {
        type: Array,
        required: true,
    }
}) 

const emit = defineEmits(["remove-Cart"])
const showNotification = inject('showNotification')

const handleRemoveCart = (item) => {
    emit("remove-Cart",item)
    showNotification(`已移除 ${item.name} `)
}
</script>