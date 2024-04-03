<template>
  <WelcomeItem>
    <div class="container">
      <h1>Vérification de l'OTP</h1>
      <p>Entrez l'OTP envoyé à votre email ou numéro de téléphone enregistré :</p>
      <div class="otp-input-container">
        <input v-for="(input, index) in 6" :key="index" v-model="otpInputs[index]" type="text" class="otp-input"
          maxlength="1">
      </div>
      <button @click="generateOTP">Générer OTP</button>
      <button @click="verifyOTP">Vérifier OTP</button>
      <p v-if="generatedOTP">OTP généré : {{ generatedOTP }}</p>
      <p v-if="successMessage" style="color: green;">{{ successMessage }}</p>
      <p v-if="errorMessage" style="color: red;">{{ errorMessage }}</p>
    </div>
  </WelcomeItem>
</template>

<script setup>
import { ref } from 'vue';
import WelcomeItem from './WelcomeItem.vue';

const otpInputs = ref(Array(6).fill(''));
let generatedOTP = '';
let successMessage = '';
let errorMessage = '';

const generateOTP = () => {
  generatedOTP = Math.floor(100000 + Math.random() * 900000).toString();
  successMessage = '';
  errorMessage = '';
  console.log("OTP généré :", generatedOTP);
};

const verifyOTP = () => {
  const userOTP = otpInputs.value.join('');
  if (userOTP === generatedOTP) {
    successMessage = "OTP vérifié avec succès !";
    errorMessage = '';
    console.log(successMessage);
  } else {
    errorMessage = "OTP incorrect ! Veuillez réessayer.";
    successMessage = '';
    console.log(errorMessage);
  }
};
</script>

<style></style>
