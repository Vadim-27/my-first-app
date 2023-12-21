<template>
  <div class="container">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: 'containerAll'
};
</script>

<style lang="scss" scoped>
.container {
  max-width: 1130px;
  margin: 0 auto;
}
</style>
