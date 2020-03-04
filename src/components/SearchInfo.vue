<template>
    <div :class="classSI ? 'first' : 'two'">
        <div>
          <span>
            <input v-model="valueI" @keyup.enter="startSearch" type="text"/>
            <span class="deleteBtn"
                  @click="deleteVal"
                  v-if="valueI.length>1">×</span>
          </span>
            <button @click="startSearch">Search</button>
        </div>
        <span>{{wordForSearch}}</span>
    </div>
</template>


<script>
    export default {
        name: 'SearchInfo',
        props: {
            classSI: Boolean,
            onStartSearch: Function,
            wordForSearch: String
        },
        data() {
            return {
                valueI: ''
            }
        },
        methods: {
            startSearch() {
                this.onStartSearch({
                    value: this.valueI
                })
            },
            deleteVal() {
                this.valueI = ''
            }
        }

    }
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .first {
        width: 100vw;
        height: 100vh;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    .two {
        width: 100vw;
        height: 150px;
        display: flex;
        flex-direction: column;
        justify-content: center;
        padding-left: 30px;
    }

    div span {
        position: relative;
    }

    .deleteBtn {
        cursor: pointer;
        width: 22px;
        position: absolute;
        right: 0;
        top: 0;
        bottom: 0;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 2rem;
    }
</style>
