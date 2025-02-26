<script setup>
import { ref, onMounted } from "vue";
import { tonConnect } from "@/utils/tonConnect";

const walletConnected = ref(false);
const userWallet = ref(null);

// Connect to the wallet (only once)
const connectWallet = async () => {
  try {
    await tonConnect.connectWallet(); // Connect the wallet
    walletConnected.value = true;
    const wallets = tonConnect.getWallets();
    if (wallets.length) {
      userWallet.value = wallets[0];
    }
  } catch (error) {
    console.error("Error connecting wallet:", error);
  }
};

// Check if wallet is connected and send transaction
const sendTransaction = async () => {
  if (!walletConnected.value) {
    await connectWallet(); // Try connecting the wallet if not connected
    if (!walletConnected.value) {
      alert("Wallet not connected. Please try again.");
      return;
    }
  }

  const transaction = {
    messages: [
      {
        address: "EQCTTadEYfaUNSyOBy9WXL4SZONkbj0gUg-YQiJrTAang7PB",
        amount: (0.01 * 1e9).toString(), // Convert to nanoTONs
        text: "Test Payment",
      },
    ],
  };

  try {
    await tonConnect.sendTransaction(transaction); // Send the transaction
    alert("Transaction sent!");
  } catch (error) {
    alert("Failed to send transaction: " + error.message);
  }
};
</script>

<template>
  <div>
    <button @click="sendTransaction" :disabled="!walletConnected">
      Send Transaction
    </button>
  </div>
</template>
