<template>
  <div class="line">
    <span :class="['triangle', { active: isActive }]" @click="handleToggle" />
  </div>
</template>

<script>
export default {
  name: 'ToggleLine',
  props: {
    isActive: {
      default: false,
      type: Boolean,
      required: true
    },
    handleToggle: {
      type: Function,
      required: true
    }
  }
}
</script>

<style lang="scss" scoped>
.line{
  width: 98%;
  height: 1px;
  background-color: #151515;
  position: relative;
  margin: 0 auto;
  .triangle{
    height: 0;
    width: 0;
    position: absolute;
    border: 25px solid transparent;
    border-top-color: #151515;
    right: 5px;
    top: 0;
    transform-origin: center top;
    transition: all ease-in-out 400ms;
    cursor: pointer;
    &.active{
      perspective: 600px;
      transform: rotateX(-180deg);
    }
  }
}
</style>
