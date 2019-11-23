<template>
  <div class="sidebar">
    <n-link class="sidebar_logo" to="/">Главная</n-link>
    <ul>
      <li>
        <n-link to="/polls">Опросы</n-link>
      </li>
      <li>
        <n-link to="/users">Пользователи</n-link>
      </li>
      <li>
        <n-link to="/black-list">Черные списки</n-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'TheSidebar'
}
</script>
