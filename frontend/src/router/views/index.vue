/* eslint-disable */
<template>
    <div v-if="username != ''">
        <board></board>
    </div>
    <div v-else>
        <div>您尚未登录，主页将不会显示任何信息。</div>
    </div>
</template>

<script>
import api from '../../api.js'
import store from '../../store'
import board from '../../components/announcement_board.vue'
export default {
    methods: {
        APItest: function() {
            api.APIgetGrade(13);
        }
    },
    computed: {
        username: function() {
            return store.getters.getUsername;
        }
    },
    components: {
        board
    }
}
//<div>index</div>
//<button @click="APItest()">APItest</button>
</script>