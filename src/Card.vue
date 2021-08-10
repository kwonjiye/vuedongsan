<template>
   <!-- <div v-for="(a, i) in 원룸들" :key="i"> -->
<div>
    <img :src="원룸.image" class="room-img">
    <h4 @click="$emit('openModal', 원룸.title)">{{원룸.title}}</h4>
    <p>{{원룸.price}}원</p>
</div>
</template>

<script>
export default {
    props : {
        원룸 : Object,
    },
    methods : {
        함수(){
            this.$emit('openModal', this.원룸.id)
        }
    }

}
</script>

<style>

</style>