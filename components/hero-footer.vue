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
    position: relative;
}


span:hover::after,
span:hover::before {
    background-color: #fff;
    transition: all 1s ease 0s;
    width: 100%;
}

span::after {
    content: "";
    width: 0;
    height: 1px;
    left: 0;
    bottom: 0;
    position: absolute;
    transition: all 1s ease 0s;
}

@keyframes dropIn {
  0% {
    top: -50%
  }
  100% {
    top: 450px
  }
}

</style>