<template>
  <div class="home">
    <Hero msg="Power Source"/>
    <HomeText/>
  </div>
</template>
<script>

import Hero from '@/components/Hero.vue'
import HomeText from '@/components/HomeText.vue'

export default {
  name: 'home',
  components: {
    Hero,
    HomeText
  }
}
</script>
