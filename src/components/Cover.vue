<script setup>
import { useStore } from '@/stores/store.js'
import { onMounted, ref } from 'vue'
import IconNBALogoMark from "../components/icons/IconNBALogoMark.vue";
import IconNBALogo from "../components/icons/IconNBALogo.vue";

const isShowCover = ref(false)
const store = useStore()

const init = () => {
    isShowCover.value = true
}

onMounted(() => {
    init()
})

const expolre = () => {
    isShowCover.value = false
    store.hideOverlay()
}

</script>
<template>
    <Transition>
        <div class="cover-container" v-show="isShowCover">
            <div class="icon-nba-logo-mark">
                <IconNBALogoMark />
            </div>

            <div class="icon-nba-logo">
                <IconNBALogo />
            </div>

            <button class="btn btn-explore" @click="expolre">
                <p>探索地圖</p>
            </button>

            <p class="footer">
                © Polish Design 磨人設計 x Zeabur <br />雲原生服務部署平台製作
            </p>
        </div>
    </Transition>
</template>

<style scoped>
.v-enter-active,
.v-leave-active {
    transition: opacity 0.5s 0.2s ease;
}

.v-enter-from,
.v-leave-to {
    opacity: 0;
}

.cover-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    position: relative;
    top: -10px;
    z-index: var(--z-index-nba-cover);
}

.icon-nba-logo-mark {
    /* margin-bottom: 18%; */
    margin-bottom: 7vh;
}

.icon-nba-logo {
    margin-bottom: 10vh;
}

.footer {
    position: fixed;
    bottom: 16px;
    text-align: center;
}

@media (max-width: 768px) {
    .cover-container {
        top: -10%;
    }
}
</style>