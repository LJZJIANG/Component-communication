<template>
    <div>
        <p><span>单价：</span><span>{{price}}</span> <button @click="downPrice">降价1元</button></p>
        <p>数量: {{count}} </p>
        
    </div>
</template>
<script>
import bus from  '../eventBus.js'
export default {
    props:{
        price:{
            type:String,
            default:''
        }
    },
    data(){
        return{
            count:10
        }
    },
    methods:{
        downPrice(){
            this.$emit('downPrice')
        }
    },
    watch:{
       price(newPrice){
          bus.$emit('priceChange',newPrice,this.count) 
       } 
    }
}
</script>
