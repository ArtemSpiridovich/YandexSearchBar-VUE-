<template>
    <div>
        <ResultSearch :resultSearch="resultSearch" :wordForSearch="wordForSearch"/>
    </div>
</template>

<script>
    import ResultSearch from './ResultSearch'

    export default {
        name: "SearchingPage",
        components: {ResultSearch},
        comments: {
            ResultSearch
        },
        props: {
            resultSearch: Array,
            wordForSearch: String
        }
    }
</script>

<style scoped>

</style>