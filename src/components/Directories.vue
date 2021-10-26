<template>
  <div>
    <directory 
      :directory='directory' 
    />
  </div>
</template>

<script>
import Directory from './Directory.vue'
export default {
  components: { Directory },
  name: 'Directories',
  props: {
    directory: {
      type: Object
    }
  }
}
</script>

<style scoped>
ul, li {
  list-style-type: none;
}
</style>