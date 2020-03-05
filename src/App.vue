<template>
    <div id="app">
        <div v-if="viewMode">
            <SearchInfo :onStartSearch="onStartSearch" :classSI="true"/>
        </div>
        <div v-else>
            <SearchInfo :onStartSearch="onStartSearch" :wordForSearch="wordForSearch" :classSI="false"/>
            <SearchingPage :resultSearch="resultSearsh" />
        </div>
    </div>
</template>


<script>
    import SearchInfo from './components/SearchInfo.vue'
    import SearchingPage from "./components/SearchingPage";

    export default {
        name: 'App',
        components: {
            SearchInfo,
            SearchingPage
        },
        data() {
            return {
                state: [
                    {
                        'name': 'vk.com',
                        'data': [["VK", "https://vk.com/login?u=2&to=YWxfaW0ucGhwP3NlbD0xMjM4MDc4MTU-", "social-networkfsadjfsd;lfajksnv;kxjz;osauhdf", 0],
                            ["VKontacte", "https://vk.com/login?u=2&to=YWxfaW0ucGhwP3NlbD0xMjM4MDc4MTU-", "social-networkfsadjfsd;lfajksnv;kxjz;osauhdf", 1],
                            ["VK.com", "https://vk.com/login?u=2&to=YWxfaW0ucGhwP3NlbD0xMjM4MDc4MTU-", "social-networkfsadjfsd;lfajksnv;kxjz;osauhdf", 2]]
                    },
                    {
                        'name': 'instagramm',
                        'data': [["Insta", "https://www.instagram.com/", "kjhgdluiugoihojh;gilfukyxjztmxcuohiku.jy,hxgmfcv.k.,jhmfgn", 0],
                            ["Instagramm", "https://www.instagram.com/", "kjhgdluiugoihojh;gilfukyxjztmxcuohiku.jy,hxgmfcv.k.,jhmfgn", 1]]
                    },
                    {
                        'name': 'telegramm',
                        'data': [["Telegramm", "https://telegram.org/", "khtxjyxkx.jhcktdlig uyfouydfiyt dliydkytdlyu dkytsdkuy", 0]]
                    }
                ],
                viewMode: true,
                wordForSearch: '',
                resultSearsh: []
            }
        },
        methods: {
            onStartSearch(data) {
                this.wordForSearch = '';
                this.resultSearsh = [];
                this.viewMode = false
                if (data.value === '') {
                    this.wordForSearch = 'search bar is empty'
                } else {
                    this.state.map(el => {
                        if (data.value.toString() === el.name) {
                            this.wordForSearch = 'search result by - "' + data.value + '"';
                            this.resultSearsh = el.data
                            return
                        } else {
                            return el
                        }
                    })
                    if(this.wordForSearch === '') {
                        this.wordForSearch = 'nothing found for - "' + data.value + '"'
                    }
                }
            }
        }
    }
</script>


<style>
    #app {
        width: 100%;
        min-height: 100vh;
    }
</style>
