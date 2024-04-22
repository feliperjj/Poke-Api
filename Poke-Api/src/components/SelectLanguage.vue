<template>
  <div class="select-language-container">
    <select v-model="selectedLanguage" @change="changeLanguage(selectedLanguage)">
      <option v-for="lang in supportedLanguages" :key="lang.code" :value="lang.code">{{ lang.name }}</option>
    </select>
    <div>{{ translations.name }}</div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const supportedLanguages = [
  { code: 'en', name: 'English' },
  { code: 'es', name: 'Spanish' },
  { code: 'pt', name: 'Portuguese' }
];

const selectedLanguage = ref('en'); 
const translations = ref({});

const changeLanguage = (languageCode) => {
  selectedLanguage.value = languageCode;
  loadTranslations(languageCode);
}

const loadTranslations = async (languageCode) => {
  const res = await fetch(`https://pokeapi.co/api/v2/language/${languageCode}`);
  const data = await res.json();
  translations.value = data.names.find(name => name.language.name === 'en').name; 
}

loadTranslations(selectedLanguage.value);
</script>



<style scoped>
.select-language-container {
  position: fixed;
  top: 20px;
  right: 20px;
  padding: 10px;
  background-color: #ffffff;
  border-radius: 8px;
  border: 1px solid #ccc; 
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  z-index: 1000;
  font-size: 16px; 
  color: #333;
}

.select-language-container select {
  width: 100%;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
  background-color: #fff;
  font-size: 16px;
  color: #333;
  outline: none; 
}

.select-language-container select:focus {
  border-color: #007bff; 
}
</style>


