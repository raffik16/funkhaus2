<template>
<div>

  <div class="timebar">
    <div class="inner-bar"></div>
  </div>

  <div class="hero-text-wrap" :class="{'is-hovering' : hoverOver }">
      <transition-group class="slider" name="slide" tag="div">
        
        <div
          v-for="number in [currentNumber]"
          :key="number"
          class="slider-parent">

          <div class="hero-title-wrap"
              @mouseenter="hoverOver = true"
              @mouseleave="hoverOver = false">

            <div class="hero-header">
                {{currentTitle}}
            </div>

            <div class="hero-sub-header">
                Sia — The Greatest
            </div>

            <div class="play">
              <span>&#x25B6;</span> Play
            </div>
          </div>

          <img :src="currentImage" />
      </div>
    </transition-group>

  </div>
</div>
</template>

<script>
export default {
  async fetch() {
      this.database = await fetch(
          "https://raw.githubusercontent.com/funkhaus/technical-assessment-round-2/master/db.json"
          // Format result as json
          ).then((res) => res.json())
    },
  
    mounted: function () {
      this.startRotation();
      this.mapData();
    },

    methods: {
      mapData: function() {
          const slideshowImages = this.database.pages.map(page => `https:${page.featuredImage.sourceUrl}`);
           this.images.push(...slideshowImages)
          console.log(slideshowImages);

          const slideshowTitle = this.database.pages.map(page => `${page.title}`);
          this.titles.push(...slideshowTitle)
          console.log(slideshowTitle);
      },

      startRotation: function() {
          this.timer = setInterval(this.next, 7000);
      },

      stopRotation: function() {
          clearTimeout(this.timer);
          this.timer = null;
      },

      next: function() {
          this.currentNumber += 1
      }
    },

     data: () => {
     return {
      database : [],
      images: [],
      titles: [],
      currentNumber: 0,
      timer: null,
      hoverOver: false, 
     }
    },
    
    computed: {
    	currentImage: function() {
        return this.images[Math.abs(this.currentNumber) % this.images.length];
      },
      currentTitle: function() {
        return this.titles[Math.abs(this.currentNumber) % this.titles.length];
      },

    },
}
</script>

<style scoped>
.timebar {
  height: 6px;
  width: 100%;
  position: absolute;
  z-index: 40;
}

.timebar .inner-bar {
  animation: fill 7s linear infinite;
  height: 100%;
  background-color: #fff;
}

.slider {
    height: 100vh;
    overflow: hidden;
    background: #000;
    position: relative;
    z-index: 10;
}

.slide-leave-to {
  overflow: hidden;
  position: relative;
  transition: transform 3s cubic-bezier(0.76, 0, 0.5, 1);
  transform: translate3d(0, -100%, 0);
  z-index: 30;
  backface-visibility: hidden;
  will-change: transform;
}

.slide-enter-to {
  overflow: hidden;
  position: relative;
  transition: transform 3s cubic-bezier(0.76, 0, 0.5, 1);
  transform: translate3d(0, -100%, 0);
  z-index: 10;
  backface-visibility: hidden;
  will-change: transform;
}

.slide-leave-to .hero-title-wrap {
  transition: top 3s cubic-bezier(0.76, 0, 0.5, 1);
  top: 100%;
}

.hero-text-wrap .play {
  opacity: 0;
  transition: opacity .25s ease-in-out 0s;
  font-family: 'lotasemibold';
  text-transform: uppercase;
  font-size: 18px;
}

.hero-text-wrap.is-hovering .play {
  opacity: 1;
  transition: opacity .25s ease-in-out 0s;
}

.play span {
  margin-right: 10px;
}

.hero-title-wrap {
    position: fixed;
    text-align: center;
    color: #fff;
    top: 350px;
    left: 50%;
    transform: translate(-50%, -50%);
    transition: top 3s cubic-bezier(0.76, 0, 0.5, 1);
    z-index: 10;
}

.slider-parent {
  position: relative;
  backface-visibility: hidden;
  will-change: transform;
  perspective: 1000;
}

.hero-header {
  font-size: 42px;
  line-height: 40px;
  font-family: 'lotasemibold';
  transition: top .25s ease-in-out 0s;
  top: 0;
  position: relative;
}

.is-hovering .hero-header {
  transition: top .25s ease-in-out 0s;
  top: -7px;
}

.hero-sub-header {
  font-size: 28px;
  transition: top .25s ease 0s;
  top: 0;
  position: relative;
}

.is-hovering .hero-sub-header {
  transition: top .25s ease 0s;
  top: -7px;
}

img {
  width: 100%;
}

/* Fill Animations */
@keyframes fill {
  0% {
    width: 0%;
  }
  100% {
    width: 100%;
  }
}

/* Media Quires for main background image. */
@media(min-width:768px) {
  .hero-title-wrap {
    top: 450px;
  }

   .hero-header {
      font-size: 72px;
      line-height: 69px;
  }

  img {
   transform: scale(3);
  }
}

@media(min-width:991px) {
  img {
   transform: scale(2);
  }
}

@media(min-width:1024px) {
  img {
   transform: scale(2.2);
  }
}

@media(min-width:1200px) {
  img {
   transform: none;
   height: 100vh;
  }
}


/* MAX Quires for main background image. */
@media(max-width:768px) {
  img {
     transform: scale(3.5);
     transform-origin: top;
  }

  .slide-enter-to {
    height: 100vh; 
    z-index: 20;
  }
  
  .slide-leave-to {
    height: 100vh;
  }
}


</style>
