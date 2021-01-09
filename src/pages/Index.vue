<template>
  <Layout>
    <nav-indicator v-if="!isMobile"/>
    <me/>
    <what-i-do/>
    <contact-me/>
  </Layout>
</template>

<script>
import Me from '~/components/Me.vue'
import WhatIDo from '~/components/WhatIDo.vue'
import ContactMe from '~/components/ContactMe.vue'
import NavIndicator from '~/components/NavIndicator.vue'

export default {
  components: { Me, WhatIDo, ContactMe, NavIndicator },
  
  data () {
    return {
      isMobile: false
    }
  },
  
  mounted () {
    window.addEventListener('resize', () => {
      this.isMobile = window.innerWidth <= 600
    })
  }
}
</script>

<style lang="scss" scoped>
</style>
