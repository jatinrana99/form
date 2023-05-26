<template class="temp">
    
    <div class="my">
        <button class="my1" v-on:click="Message()">{{ name }}</button>
    </div>
</template>

<script>
export default {
    name:`BaseButton`,
    data(){

    },
    props:{
        Message:Function,
        name:String
        
    },
    methods:{
        message(){
            alert("Hello From Child");
        }
    }
}
</script>