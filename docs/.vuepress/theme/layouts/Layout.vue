<template>
  <div class="theme-container">
    <Header />
    <Content class="theme-content" />
    <Footer />
  </div>
</template>

<style lang="stylus" scoped>


.theme-container {
  display: flex;
  min-height: 100vh;
  flex-direction: column;
}
.theme-content {
  flex: 1;
  padding: 1em 0;
}
</style>