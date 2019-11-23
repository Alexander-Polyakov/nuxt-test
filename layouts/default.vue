<template>
  <div class="app-container">
    <TheSidebar />
    <div class="app-content">
      <nuxt />
    </div>
  </div>
</template>

<script>
import TheSidebar from '@/components/TheSidebar'

export default {
  components: {
    TheSidebar
  }
}
</script>

<style>
html,
body {
  margin: 0;
  height: 100%;
  width: 100%;
}
.app-container {
  max-width: 1200px;
  margin: 0 auto;
  position: relative;
  display: flex;
}

.app-content {
  flex-shrink: 0;
  flex-basis: 100%;
}

.polls-form__title {
  background: #ccc;
  padding: 20px;
  margin-bottom: 20px;
  font-size: 15px ;
}
.polls-form__add {
  width: 100%;
  padding: 50px;
  text-align: center;
  border: 1px solid #ccc;
  border-radius: 5px ;
  cursor: pointer;
  color: green;
  margin-top: 20px;
}

.polls-item {
  padding: 20px;
  border: 1px solid #ccc; 
}

.polls-item__header {
  display: flex;
  margin-bottom: 20px;
}

.polls-item__main-item {
  display: flex;
  margin-bottom: 15px;
}

.polls-item__left {
  width: 300px;
}

.polls-item__footer {
  display: flex;
  justify-content: space-between;
  padding-left: 300px;
}

.polls-item__add-value, .polls-item__remove-poll {
  padding: 10px;
  border: 1px solid #ccc;
  cursor: pointer;
}

.polls-item__remove-poll{
  margin-top: 20px;
  width: 200px;
}

</style>
