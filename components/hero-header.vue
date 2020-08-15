<template>
  <div class="header-liner">
    <div class="logo-wrap">
      <img alt="Skull" src="~/static/images/skull.png" class="logo">
      <span class="exile">
        Exile
      </span>
    </div>

    <div class="menu" :class="{'is-hovering-finishing' : finishingHoverOver, 'is-hovering-editors' : editorsHoverOver }">
      <span class="editors-item"
            @mouseenter="editorsHoverOver = true"
            @mouseleave="editorsHoverOver = false">
        Editors
      </span>
      <span class="bar"></span>
      <span class="finishing-item"
            @mouseenter="finishingHoverOver = true"
            @mouseleave="finishingHoverOver = false">
        Finishing
      </span>
    </div>
  </div>
</template>

<script>
export default {
  name: "hero-header",
  data: () => {
    return {
    finishingHoverOver: false, 
    editorsHoverOver: false, 
    }
  },
}
</script>

<style scoped>
.header-liner {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  width: 100%;
  color: #fff;
}

.logo-wrap {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}

.logo {
  max-width: 40px;
}

.exile {
  font-family: 'Bitter', serif;
  text-transform: uppercase;
  letter-spacing: 5px;
  margin-left: 20px;
}

.bar {
  background: #fff;
  height: 1px;
  width: 90px;
  margin: 0 25px;
  position: absolute;
  right: 28px;
  top: 60px;
  transition: all .3s ease-in-out 0s;
}

.menu {
  display: flex;
  align-items: center;
  justify-content: space-between;
  font-family: 'lotasemibold';
  text-transform: uppercase;
  font-size: 18px;
}

.editors-item {
  position: relative;
  transition: left .3s ease-in-out 0s;
  left: 0;
}

span.editors-item {
      margin-right: 15px;
  }


@media(min-width:768px) {

  .bar {
    background: #fff;
    height: 1px;
    width: 100px;
    margin: 0 25px;
    position: absolute;
    right: 90px;
    top: auto;
    transition: all .3s ease-in-out 0s;
}
  span.editors-item {
      margin-right: 150px;
  }


.is-hovering-editors .editors-item {
  transition: left .3s ease-in-out 0s;
  left: -20px;
}

.is-hovering-editors .bar {
  right: 90px;
  width: 110px;
}

.finishing-item {
  position: relative;
  transition: right .3s ease-in-out 0s;
  right: 0;
}

.is-hovering-finishing .bar {
  right: 80px;
  width: 110px;
}

.is-hovering-finishing .finishing-item {
  transition: right .3s ease-in-out 0s;
  right: -20px;
}

}

</style>