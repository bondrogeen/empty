<template>
  <div id="app" class="app">
    <div class="app__inner">
      <router-view />
    </div>
  </div>
</template>

<style lang="scss">
.app {
  height: 100%;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;

  &__inner {
    height: 100%;
    width: 100%;
    min-width: 360px;
    max-width: 600px;
    padding: 20px;
  }
}
</style>
