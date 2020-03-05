<template>
    <div>
        <div class="content" :key="item" v-for="item in resultSearch">
            <div ><h2>{{item[0]}}</h2>
                <a :href="item[1]" target="_blank">{{item[1]}}</a>
                <span>{{item[2]}}</span></div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "ResultSearch",
        props: {
            resultSearch: Array
        }
    }
</script>

<style scoped>
    .content {
        width: 400px;
        height: 200px;
        display: flex;
        flex-direction: column;
    }
</style>