<template>
  <div class="app-container">
    <TheSidebar />
    <div class="app-content">
      <!-- <DefaultNav /> -->
      <nuxt />
    </div>
  </div>
</template>

<script>
import DefaultNav from '@/components/DefaultNav'
import TheSidebar from '@/components/TheSidebar'

export default {
  components: {
    TheSidebar,
    DefaultNav
  }
}
</script>
