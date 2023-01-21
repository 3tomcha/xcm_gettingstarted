<script setup lang="ts">
import abi from "@/abi/xtokensABI.js";
import { ethers } from "ethers";
const PRIVATE_KEY = import.meta.env.PRIVATE_KEY;

const provider = new ethers.providers.JsonRpcProvider("https://rpc.api.moonbeam.network");
const signer = new ethers.Wallet(PRIVATE_KEY, provider);
const xTokens = new ethers.Contract(
  '0x0000000000000000000000000000000000000804',
  abi,
  signer
);
async function transferToAlice() {
  const transaction = await xTokens.transfer(
    xcUINIT_ADDRESS,
    '1000000000000',
    ALICE_RELAY_ACC,
    '1000000000'
  );
  await transaction.wait();
  console.log(transaction);
}
</script>

<template>
  <p>loaded</p>
</template>