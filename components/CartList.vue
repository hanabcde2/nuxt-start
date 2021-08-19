<template>
  <v-row justify="center" align="center">
        <v-col v-for="cartItem in $store.state.cartItems" :key="cartItem.id" cols='12' lg='4' md='4' sm='6' >
            <v-card width="100%" hover class="pa-3">
                <v-card-text>
                    <img :src="cartItem.imageUrl" width="100%" :alt="cartItem.name" />
                    <div class="d-flex align-center flex-column">
                        <span>{{cartItem.name}}</span> 
                        <span>{{cartItem.price}}</span>
                    </div>
                </v-card-text>
            </v-card>
        </v-col>
    </v-row>
</template>

<script>
import { FETCH_CART_ITEMS} from '@/store'

export default {
    // async asyncData({store}) {
    //    await store.dispatch(FETCH_CART_ITEMS)
    // },
    async fetch(){
       await this.$store.dispatch(FETCH_CART_ITEMS)
    }
}
</script>

<style>

</style>