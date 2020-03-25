<template>
  <div>
    <div class="progress-bar">
      <div class="progress-bar__percent">{{ progress }}%</div>
      <div class="progress-bar__bar">
        <div class="progress-bar__line progress-bar__line_color progress-bar_animated" :style="{width: progress + '%'}"></div>
      </div>
    </div>
    <button @click="progress += 10">+ 10</button>
  </div>

</template>

<script>
export default {
  name: 'progressBar',
  props: {},
  data () {
    return {
      progress: 10
    }
  }
}
</script>

<style scoped lang="sass">
</style>
