<script>
  export default {
  props: {
    iconName: {
      type: String,
      default: 'box'
    },
    width: {
      type: [Number, String],
      default: 18
    },
    height: {
      type: [Number, String],
      default: 18
    },
    iconColor: {
      type: String,
      default: 'currentColor'
    }
  }
}
</script>

<template>
  <svg width="42" 
    height="42"
    viewBox="0 0 42 42"
    xmlns="http://www.w3.org/2000/svg"
    :aria-labelledby="iconName"
    role="presentation"
  >
    <title
      :id="iconName"
      lang="en"
    >{{iconName}} icon</title>
    <g :fill="iconColor">
      <slot />
    </g>
  </svg>
  
</template>

<style scoped>
</style>
