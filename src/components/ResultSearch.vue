<template>
    <div>
        <div class="content" :key="item[3]" v-for="item in resultSearch">
            <div ><a :href="item[1]"><h2>{{item[0]}}</h2></a>
                <a class="href" :href="item[1]" target="_blank">{{item[1]}}</a>
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
        height: max-content;
        display: flex;
        flex-direction: column;
        padding-left: 30px;
        margin: 10px 0;
    }

    h2{
        font-family: Arial, Helvetica, sans-serif;
        font-weight: 400;
        font-size: 18px;
        line-height: 24px;
        margin: 8px 0;
    }

    a {
        text-decoration: none;
        transition: all .3s linear;
    }

    a:hover {
        color: red!important;
    }

    .href {
        color: #070;
        font-family: Arial,Helvetica,sans-serif;
        white-space: nowrap;
        max-width: 160px;
        display: block;
        text-overflow: ellipsis;
        overflow: hidden;
        font-weight: 700;
        font-size: 14px;
        line-height: 17px;
    }
</style>