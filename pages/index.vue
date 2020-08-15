<template>
  <!-- Main Parent Index Div -->
  <div class="main-parent">

    <header class="header-wrap">
      <!-- Import hero header -->
      <hero-header />
    </header>
    
    <!-- Import hero images + titles -->
    <hero />

    <footer class="footer-wrap">
      <!-- Import hero footer -->
      <hero-footer />
    </footer>
  </div>
</template>

<script>
export default {
  // Fetch API data
  async fetch() {
    this.db = await fetch(
        "https://raw.githubusercontent.com/funkhaus/technical-assessment-round-2/master/db.json"
        // Format result as json
        ).then((res) => res.json())
  },
  head() {
    return {
      title: this.db.siteMeta.title, // Grab title from API
      meta: [
        {
          hid: 'description', //  Must use hid
          name: 'description', // Type of meta property
          content: this.db.siteMeta.description // Insert description from API
        },
        {
          hid: 'og-image', //  Must use hid
          property: 'og-image',  // Type of meta property
          content: this.db.siteMeta.thumbnail // Insert description from API
        }
      ]
    }
  },
  data: () => {
    return {
      db : [], // Set top level array
    }
  },
}
</script>

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