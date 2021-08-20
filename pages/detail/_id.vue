<template>
  <div>

      <v-card >
        <v-card-title class="d-flex justify-center">
          {{product.name}}
        </v-card-title>
        <v-card-text >
          <div class="d-flex justify-center">
            <img :src="product.imageUrl" width="90%" :alt="product.name" />
          </div>
          <div class="d-flex justify-center">
            {{product.price}}
          </div>
        </v-card-text>
        <v-card-actions class="d-flex justify-center">
          <v-btn @click="addToItem">
            장바구담기
          </v-btn>
        </v-card-actions>
      </v-card>
  </div>
</template>

<script>

import { fetchProductById, createCartItem } from '@/api/index'

export default {
  async asyncData({ params }){
    let product = await fetchProductById(params.id);
    
    product = product.data
    return {product}
  }, 
  head: {
    title: 'Shopping Item Detail',
    meta: [
      { 
      hid: 'description', 
      name: 'description',
      content: '이 상품은 ~~입니다' 
      },
    ],
    link: [
      { rel: 'icon', type: 'image/x-icon', href: '/favicon.ico' }
    ]
  },
  methods: {
  async addToItem(){
      const {data} = await createCartItem(this.product);
      this.$store.commit('addCartItem', data);
      this.$router.push('/cart');
    }
  }

}
</script>

<style>

</style>