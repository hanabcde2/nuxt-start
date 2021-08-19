<template>
    <v-row justify="center" align="center">
        <nuxt-link to="/cart"><v-card hover class="cart rounded-circle d-flex justify-center align-center" width="70" height="70">
            <v-icon >mdi-tag-plus</v-icon>
          </v-card></nuxt-link>
        <v-col cols="12" class="d-flex justify-center">
            <!-- :search-keyword="searchKeyword" -->
            

            <search-input v-model="searchKeyword" @search="searchProducts" />
            
        </v-col>
        <v-col v-for="product in products" :key="product.id" cols='12' lg='4' md='4' sm='6' >
            <v-card width="100%" hover class="pa-3" @click="moveToDetailPage(product.id)">
                <v-card-title class="d-flex justify-center">
                    <span>{{product.name}}</span> 
                </v-card-title>
                <v-card-text>
                    <img :src="product.imageUrl" width="100%" :alt="product.name" />
                    <div class="d-flex align-center flex-column">
                        <span>{{product.price}}</span>
                    </div>
                </v-card-text>
            </v-card>
        </v-col>
    </v-row>
</template>
<script>

import axios from 'axios'
import SearchInput from '~/components/SearchInput.vue';
import { fetchProductByKeyword } from '@/api/index'
// import ProductList from '~/components/ProductList.vue'

export default {
  components: { SearchInput },
  // components:{ ProductList },
    async asyncData() {
    const response = await axios.get(`http://localhost:3000/products`);
    const products = response.data.map( item => ({
      ...item,
      imageUrl: `${item.imageUrl}?random=${Math.random()}`
    }))
    return { products }
  },

  data(){
      return{
          searchKeyword:''
      }
  },
  methods:{
    moveToDetailPage(id){
    this.$router.push(`detail/${id}`);
    },
    async searchProducts() {
        const response = await fetchProductByKeyword(this.searchKeyword)
        this.products = response.data
    }
  }
  
}


</script>
<style lang="scss" scoped>

.cart{
  position:fixed;
  right: 7%;
  top: 85vh;
  z-index: 9;
  
}
.cart:hover{
  transition: .3s;
  width:80px !important;
  height:80px !important;
}
</style>