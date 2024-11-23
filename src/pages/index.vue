<template>
    {{ $store.state.user.username }}
    <el-button @click="handleLogout">退出登录</el-button>
</template>

<script setup>
import { ref } from "vue"
import { logout } from '~/api/manager'
import { showModal, toast } from "~/composables/util";
import { useRouter } from "vue-router";
import { useStore } from "vuex";
const router = useRouter()
const store = useStore()
function handleLogout() {
    showModal("是否退出登录？").then(res => {
        logout()
            .finally(() => {
                store.dispatch("logout")
                router.push('/login')
                toast('退出登录成功')
            })

    })
}
// import CountTo from "~/components/CountTo.vue";
// import IndexNavs from "~/components/IndexNavs.vue";
// import IndexChart from "~/components/IndexChart.vue";
// import IndexCard from "~/components/IndexCard.vue";
// import {
//     getStatistics1,
//     getStatistics2
// } from "~/api/index.js"

const panels = ref([])
// getStatistics1()
//     .then(res => {
//         panels.value = res.panels
//     })

const goods = ref([])
const order = ref([])
// getStatistics2().then(res=>{
//     goods.value = res.goods
//     order.value = res.order
// })
</script>