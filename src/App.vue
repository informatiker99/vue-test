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
const vibrate = ()=>{

// چک کردن اینکه آیا دستگاه از ویبره پشتیبانی می‌کند یا نه
if ("vibrate" in navigator) {
    // ویبره به مدت 1000 میلی‌ثانیه (1 ثانیه)
    navigator.vibrate(1000);
} else {
    console.log("ویبره پشتیبانی نمی‌شود.");
}
    }


</script>

<template>
    <button @click="vibrate">Connect</button>
</template>


