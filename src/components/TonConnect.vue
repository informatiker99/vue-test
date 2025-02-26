<script setup>
import { ref, onMounted } from "vue";
import { tonConnect } from "@/utils/tonConnect";

const walletConnected = ref(false);
const userWallet = ref(null);

// Function to connect the wallet
const connectWallet = async () => {
  await tonConnect.connectWallet();
};

// Check if a wallet is already connected
onMounted(() => {
  const wallets = tonConnect.getWallets();
  console.log(wallets,'55')
  if (wallets.length) {
    userWallet.value = wallets[0];
    walletConnected.value = true;
  }
});
</script>

<template>
  <div>
    <button v-if="!walletConnected" @click="connectWallet">
      Connect Wallet
    </button>
    <p v-if="walletConnected">Connected: {{ userWallet?.address }}</p>
  </div>
</template>
