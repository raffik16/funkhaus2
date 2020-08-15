<template>
  <div class="main-parent">
    <header class="header-wrap">
      <hero-header />
    </header>

    <hero />

    <footer class="footer-wrap">
      <hero-footer />
    </footer>
  </div>
</template>

<style scoped>
.header-wrap {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  position: absolute;
  z-index: 40;
  width: 90%;
  left: 50%;
  margin-left: -45%;
  top: 30px;
}

.footer-wrap {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  position: absolute;
  z-index: 40;
  width: 90%;
  left: 50%;
  margin-left: -45%;
  bottom: 30px;
}
</style>