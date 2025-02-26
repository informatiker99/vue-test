<script setup>
import { onMounted } from 'vue'

const prefix = 'ton://'
const amount = 0.01 *1e9 
const address=  'UQAsV3nfqjnd-yk9rMlhR1NSsoCjqYbdgJTFAutt-PRC1Gf-'
const text = '5184890136'

const redirectUri = `${window.location.origin}/return_after_receive`

    const openLik = ()=>{
        const url = `${prefix}transfer/${address}?amount=${amount}&text=${text}`
        window.open(url, '_blank')
    }

onMounted(() => {
  const urlParams = new URLSearchParams(window.location.search)
  const transactionHash = urlParams.get('transaction_hash')  
  if(transactionHash){

      console.log(transactionHash,'555');
    }else{
        console.log('no**');
        
    }

  
})
</script>

<template>
    <button @click="openLik">Connect</button>
</template>


