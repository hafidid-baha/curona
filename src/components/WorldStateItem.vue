<template>
    <transition name="fade">
        <div class="col-md-2 col-4 bg-dark text-white m-1 item rounded text-center p-2">
            <h6>{{title}}</h6>
            <span class="p-2 mt-1 d-block">{{count}}</span>
        </div>
    </transition>
</template>
<script>
export default {
    name:'WorldStateItem',
    props:{
        title: String,
        count: Number
    }
}
</script>
<style scoped>
    .item{
        height: 100px;
    }
    .fade-enter-active, .fade-leave-active {
        transition:all .5s ease;
        transition:all .5s ease;
        transform: scale(1);
    }
    .fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
        opacity: 0;
        transform: scale(0);
    }
</style>