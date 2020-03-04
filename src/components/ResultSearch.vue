<template>
    <div>
        <div class="content">
            <h2>{{resultSearch[0]}}</h2>
            <a :href="resultSearch[1]" target="_blank">{{resultSearch[1]}}</a>
            <span>{{resultSearch[2]}}</span>
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