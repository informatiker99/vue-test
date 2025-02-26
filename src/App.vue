<script setup>
import { onMounted } from 'vue'

const PREFIX = 'ton://'
const AMOUNT = 0.01 * 1e9 
const ADDRESS=  'EQCTTadEYfaUNSyOBy9WXL4SZONkbj0gUg-YQiJrTAang7PB'
const TEXT = '5184890136'

const redirectUri = `${window.location.origin}/return_after_receive`

    const openLik = ()=>{
        const url = `${PREFIX}transfer/${ADDRESS}?amount=${AMOUNT}&text=${TEXT}`

        window.open(url)
    }


</script>

<template>
    <button @click="openLik">Connect</button>
</template>


