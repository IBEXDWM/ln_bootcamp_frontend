<template>
    <div
        class="w-fit h-fit p-2 flex justify-center bg-primary-100 border rounded-lg border-primary-400"
    >
        <vue-qr
            :logo-src="logo"
            :text="data"
            :size="size"
            :logo-scale="0.25"
            :margin="0"
        />
    </div>
</template>

<script setup lang="ts">
import vueQr from 'vue-qr/src/packages/vue-qr.vue'

defineProps({
    data: { type: String, default: 'https://www.poweredbyibex.io' },
    logo: { type: String, default: '/img/logos/logo.png' },
    size: { type: Number, default: 250 },
})
</script>
