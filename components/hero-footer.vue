<template>
    <div class="footer-liner">
        <span>
            Instagram
        </span>
        <span>
            Contact
        </span>
    </div>
</template>

<script>
export default {
    name: "hero-footer"
}
</script>

<style scoped>
.footer-liner {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  width: 100%;
  color: #fff;
}

span {
    font-family: 'lotasemibold';
    text-transform: uppercase;
    font-size: 14px;
}
</style>