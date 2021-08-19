<template>
    <div>
        <div class="content">
            <input 
                type="text" 
                :value="value"
                @input="$emit('input', $event.target.value)"
                class="input pl-1"
            >
            <v-btn elevation="0" class="btn" @click="$emit('search')">
                
                검색</v-btn>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        value: {
            type: String,
            default: () => '',
        },
    },
}
</script>

<style>
.input{
    height: 100%;
    width: 100%;
 
}
.input:focus{
    border: 0px solid red !important;
    
}

.btn{
    position:absolute;
    height: 95% !important;
    top:1px;
    right: 1px;

    


}
.content{
    border: 1px solid black;
    height: 40px;
    width: 250px;
  
    position: relative;
}
</style>