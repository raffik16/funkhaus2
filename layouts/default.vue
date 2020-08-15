<template>
  <Nuxt />
</template>

<style>

@font-face {
  font-family: 'lotareg';
  src: url('~static/fonts/lotagrotesquealt1-regular-webfont.woff'); 
  src: url('~static/fonts/lotagrotesquealt1-regular-webfont.woff2') format('woff2'),
}

@font-face {
  font-family: 'lotasemibold';
  src: url('~static/fonts/lotagrotesquealt1-semibold-webfont.woff'); 
  src: url('~static/fonts/lotagrotesquealt1-semibold-webfont.woff2') format('woff2'),
}

html {
  font-family: 'lotareg', arial;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}
</style>
