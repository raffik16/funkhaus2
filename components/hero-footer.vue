<template>
    <div class="footer-liner" :class="{'ig-hovering' : hoverOverIg, 'contact-hovering' : hoverOverContact }">
        <span class="ig-span"
              @click="hoverOverIg = true"
              @mouseenter="hoverOverIg = true"
              @mouseleave="hoverOverIg = false">
            Instagram
        </span>
        <span class="contact-span"
              @click="hoverOverContact = true"
              @mouseenter="hoverOverContact = true"
              @mouseleave="hoverOverContact = false">
            Contact
        </span>
    </div>
</template>

<script>
export default {
    name: "hero-footer",
    data: () => {
    return {
      hoverOverIg: false, // Default hoverOverIg = false
      hoverOverContact: false
    }
  },
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

/* span:hover::after,
span:hover::before {
    background-color: #fff;
    transition: all 1s ease 0s;
    width: 100%;
} */

.ig-hovering .ig-span::after,
.contact-hovering .contact-span::after {
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
</style>