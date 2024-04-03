<script setup>
defineProps({
  msg: {
    type: String,
    required: true
  },
  generatedOTP: {
    type: String, // Type de données pour l'OTP généré
    default: ''   // Valeur par défaut de l'OTP généré
  }
})
</script>

<template>
  <div class="greetings">
    <h1 class="green">{{ msg }}</h1>
    <h3>
      OTP verification: {{ generatedOTP }}
      <a href="https://vitejs.dev/" target="_blank" rel="noopener">Vu</a> +
      <a href="https://vuejs.org/" target="_blank" rel="noopener">JS</a>.
    </h3>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {

  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
