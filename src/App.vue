<template>
  <div>
    <h2>Generador de texto de OpenAI GPT-3</h2>
    <form @submit.prevent="generateText">
      <label for="prompt">Ingrese su texto de entrada:</label>
      <textarea id="prompt" v-model="prompt"></textarea>
      <button type="submit">Generar texto</button>
    </form>
    <div v-if="generatedText">
      <h3>Texto generado:</h3>
      <p>{{ generatedText }}</p>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      prompt: '',
      generatedText: ''
    }
  },
  methods: {
    async generateText() {
      const apiKey = ''
      const apiUrl = 'https://api.openai.com/v1/engines/davinci-codex/completions'
      const response = await axios.post(apiUrl, {
        prompt: this.prompt,
        max_tokens: 100,
        temperature: 0.5
      }, {
        headers: {
          Authorization: `Bearer ${apiKey}`
        }
      })
      this.generatedText = response.data.choices[0].text
    }
  }
}
</script>