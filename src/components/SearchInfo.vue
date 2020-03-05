<template>
    <div class="contentSearchBar" :class="classSI ? 'first' : 'two'">
        <div>
            <div class="text">
                <span class="yandex">Яндекс</span>
                <form @submit.prevent="" class="inputAndBtn"><input :ref="'input'" v-model="valueI" @keyup.enter="startSearch" autofocus type="text"/>
                    <span class="deleteBtn"
                          @click="deleteVal"
                          v-if="valueI.length>1">×</span>
                    <button @click="startSearch">Search</button>
                </form>
            </div>
        </div>
        <span class="result">{{wordForSearch}}</span>
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
                this.$nextTick(() => {
                    this.$refs['input'].focus();
                });
            }
        }

    }
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .contentSearchBar {
        width: 100vw;
        height: 100vh;
        display: flex;
        flex-direction: column;
        justify-content: center;
    }

    .first {
        align-items: center;
    }

    .two {
        width: max-content;
        height: 151px;
        padding-left: 30px;
    }

    .inputAndBtn {
        position: relative;
        padding-bottom: 10px;
    }

    input {
        display: inline-block;
        box-sizing: border-box;
        height: 40px;
        width: 250px;
        border: 2px solid #fc0;
        border-radius: 4px;
        background: #fff;
        outline: none;
        padding-left: 11px;
        font-family: 'Arial', sans-serif;
        font-size: 18px;
        font-weight: 400;
    }

    button {
        outline: none;
        width: 80px;
        height: 40px;
        padding: 2px 0 2px 5px;
        font: 16px/35px arial, sans-serif;
        border: none;
        background-color: #fc0;
        position: relative;
        border-radius: 0 2px 2px 0;
    }

    button::after {
        content: '';
        position: absolute;
        background-color: #fc0;
        width: 4px;
        height: 40px;
        left: -4px;
        top: 0;
    }

    .yandex {
        margin-right: 10px;
    }

    .yandex:first-letter {
        color: red;
    }

    .text {
        font-family: 'Arial', sans-serif;
        font-weight: 400;
        font-size: 3rem;
        display: flex;
        align-items: center;
    }

    .result {
        display: flex;
        justify-content: center;
    }

    .deleteBtn {
        cursor: pointer;
        width: 22px;
        position: absolute;
        right: 87px;
        top: 21px;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 2rem;
    }
</style>
