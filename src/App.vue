<template>
    <div>
      <div>
        <button @click="changeAlien">
          Alien speaks...
        </button> <br>

        <transition name="fade" mode="out-in">
          <div v-bind:key="count">
            <div class="float">
              <img :src="aliens[count]" alt="">
            </div>
            <p class="quote">
              {{ tips[count] }}
            </p>
          </div>
        </transition>
        
      </div>
    </div>
</template>

<script>
export default {
  name: 'App',
  data: function () {
    return  {
      count: 0,
      showing: true,
      aliens: [
        '/static/Alien_01.png',
        '/static/Alien_02.png',
        '/static/Alien_03.png',
      ],
      tips: [
        'Life is short, don\'t be lazy',
        'Work hard, be nice',
        'Team work makes the dream work'
      ]
    }
  },
  methods: {
    changeAlien: function () {
      this.showing = !this.showing
      this.count++

      if (this.count >= this.aliens.length) {
        this.count = 0;
      }
    }
  }
}
</script>
<style lang="scss">
  // Transitions
  .fade-enter-active, .fade-leave-active {
    transition: all 1s;
  }

  .fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
    opacity: 0;
    transform: translateX(100px) ;
  }

  // Extras
  body {
    margin: 20px 50px;
  }

  .panel {
    width: 760px;
    display: inline-block;
    vertical-align: top;
    margin: 20px;
  }

  .quote {
    font-size: 50px;
  }

  .float {
    float: left;
    width: 300px;
  }
</style>
