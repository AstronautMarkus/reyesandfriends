<template>
  <div>
    <v-btn icon @click="toggleTheme">
      <v-icon>{{ currentTheme === 'light' ? 'mdi-weather-night' : 'mdi-white-balance-sunny' }}</v-icon>
    </v-btn>
  </div>
</template>

<script>
import { useTheme } from 'vuetify'

export default {
  name: 'Lamp',
  setup() {
    const theme = useTheme()
    const currentTheme = theme.global.name

    const savedTheme = localStorage.getItem('theme')
    if (savedTheme) {
      theme.global.name.value = savedTheme
    }

    const toggleTheme = () => {
      const newTheme = currentTheme.value === 'light' ? 'dark' : 'light'
      theme.global.name.value = newTheme
      localStorage.setItem('theme', newTheme)
    }

    return {
      currentTheme,
      toggleTheme,
    }
  },
}
</script>
