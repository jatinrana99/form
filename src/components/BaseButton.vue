<template class="temp">
    
    <div class="my">
        <button class="my1" v-on:click="alert">{{ name }}</button>
    </div>
</template>

<script>
export default {
    name:`BaseButton`,
    props:[
        'alert',
        'name' 
    ]
}
</script>