<template>
  <header class="header">
    <router-link to="/" >UI Kit</router-link>
  </header>
</template>

<style lang="scss" scoped>
  .header {
    background-color: #fff;
    font-weight: bold;
    padding: 0 20px;
    box-shadow: 0 0 10px rgba(0, 0, 0, .07);
    height: 62px;
    display: flex;
    align-items: center;
    z-index: 1;
    position: fixed;
    width: 100%;
    top: 0;
  }
</style>