<template>
  <div>
    <h1>NAIROBI LN BOOTCAMP</h1>
    <h3>CHALLENGE 1: Get Account Details</h3>
    <h2>ACCOUNT: {{ accountName }}</h2>
    <h2>Balance: {{ accountBalance }}</h2>
    <hr />

    <h3>CHALLENGE 2: Generate Invoice</h3>
    <qr-code :data="bolt11Invoice" />
    <span>{{ bolt11Invoice }}</span>
    <hr />

    <h3>CHALLENGE 3: Pay Outside Invoice (Wallet of Satoshi or Blink)</h3>
    <button @click="payInvoice">PAY INVOICE</button>
  </div>
</template>

<script setup lang="ts">
import qrCode from "~~/components/qr-code.vue";

const bolt11Invoice = ref("lnbc....");
const accountId = ref("enter accountId from IBEX sandbox");
const accountName = ref("account1");
const accountBalance = ref(0);
const invoiceAmount = ref(1000);

const refreshAccountData = () => {
  setTimeout(() => getAccountDetails, 3000);
};

//CHALLENGE 1
const getAccountDetails = async () => {
  // STEP 1) CALL IBEXHUB API EITHER DIRECTLY OR TO AN LN_BOOTCAMP BACKEND
  //docs -> https://docs.ibexmercado.com/reference/get-account-details
  //api endpoint -> https://api-sandbox.poweredbyibex.io/v2/account/{accountId}
  //make request using https://nuxt.com/docs/getting-started/data-fetching#usefetch
  // STEP 2) UPDATE ACCOUNT NAME AND BALANCE
  // accountName.value = response.data (from api response STEP 1)
  // accountBalance.value = response.data (from api response STEP 1)
};

//CHALLENGE 2
const generateInvoice = async () => {
  // STEP 1) CALL IBEXHUB API EITHER DIRECTLY OR TO AN LN_BOOTCAMP BACKEND
  //docs -> https://docs.ibexmercado.com/reference/add-invoice
  //api endpoint -> https://api-sandbox.poweredbyibex.io/v2/invoice/add
  //POST (/ibex/add-invoice, data: {amount: invoiceAmount})

  //make request using https://nuxt.com/docs/getting-started/data-fetching#usefetch

  // STEP 2) DISPLAY INVOICE DATA IN QR CODE
  // bolt11Invoice.value = response.data (from api response STEP 1)
  console.log("hi");
  refreshAccountData();
};

//CHALLENGE 3
const payInvoice = async () => {
  //STEP 1) CALL IBEXHUB API EITHER DIRECTLY OR TO AN LN_BOOTCAMP BACKEND
  //docs -> https://docs.ibexmercado.com/reference/add-invoice
  //api endpoint -> https://api-sandbox.poweredbyibex.io/v2/invoice/add

  await getAccountDetails();
};

onMounted(async () => {
  await getAccountDetails();
  await generateInvoice();
});
</script>
