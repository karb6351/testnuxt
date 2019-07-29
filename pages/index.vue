<template>
  <div class="main-container">
    <div :class="['top', { active }]">
      <transition name="fade">
        <Magnet v-show="!active" />
      </transition>
      <transition name="fade">
        <ShowCase v-show="active" />
      </transition>
    </div>
    <div :class="['bottom', { active }]">
      <ToggleLine :is-active="active" :handle-toggle="toggle" />
      <div class="logo-wrapper">
        <div class="logo">
          logo
        </div>
      </div>
      <div v-show="active" class="container">
        123
      </div>
    </div>
  </div>
</template>

<script>
import Magnet from '~/components/Magnet'
import ToggleLine from '~/components/ToggleLine'
import ShowCase from '~/components/ShowCase'

export default {
  name: 'HomePage',
  components: {
    Magnet,
    ToggleLine,
    ShowCase
  },
  data () {
    return {
      active: false
    }
  },
  methods: {
    toggle () {
      this.active = !this.active
    }
  }
}
</script>

<style lang="scss" scoped>
  .main-container{
    display: flex;
    flex-direction: column;
    min-height: 100vh;
    .top{
      flex: 1 0 100%;
      justify-content: center;
      display: flex;
      align-items: center;
      transition: all ease-in-out 400ms;
      &.active{
        flex: 0 0 auto;
      }
    }
    .bottom{
      transition: all ease-in-out 400ms;
      flex: 0 0 min-content;
      width: 100%;
      &.active{
        flex: 1 1 100%;
      }
    }
  }
  .logo-wrapper{
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    padding: 20px 0;
    height: 100px;
    .logo {

    }
  }

  .fade-enter-active, .fade-leave-active {
    transition: all 200ms;
  }
  .fade-enter, .fade-leave-to {
    opacity: 0;
  }
</style>
