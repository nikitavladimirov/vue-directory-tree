<template>
  <div>
    <ul>
      <li>
        <directories
          :directory='root'
        >
        </directories>
      </li>
    </ul>
  </div>
</template>

<script>
import root from "../../public/static/node_modules.json"
import Directories from "./Directories.vue"
export default {
  components: { Directories },
  name: 'DirectoryTree',
  data: () => {
    return {
      root: root
    }
  },
}
</script>

<style scoped>
ul, li {
  list-style-type: none;
}
</style>