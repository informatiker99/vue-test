<script setup>
const prefix = 'ton://'
const amount = 0.01 *1e9 
const address=  'UQAsV3nfqjnd-yk9rMlhR1NSsoCjqYbdgJTFAutt-PRC1Gf-'
const text = '5184890136'
    const openLik = ()=>{
    window.open(`${prefix}/transfer/${address}?amount${amount}$text=${text}`)
    }

</script>

<template>
    <button @click="openLik">Connect</button>
</template>


