<template>
  <li class="item" v-bind:class="checkType()">
    <span 
      @click="itemClick()"
    >
      {{ directory.name }}
    </span>

    <ul class="sub-directories" v-if="directory.contents && directory.contents.length > 0" v-show="isExpanded">
      <directory 
        v-for="(child, i) in directory.contents"
        :key="`${child}-${i}`" 
        :directory="child">
        </directory>
    </ul>
    <!-- <div class="directory-empty" v-else v-show="!directory.leaf && directory.expanded">No Data</div> -->
  </li>
</template>

<script>
export default {
  name: 'Directory',
  props: {
    directory: Object
  },
  data () {
    return {
      isExpanded: false
    }
  },
  methods: {
    checkType() {
      switch (this.directory.type) {
        case 'file': return 'is-file';
        case 'directory': return 'is-directory';
        case 'link': return 'is-link';
      }
    },
    itemClick () {
      if (!this.directory.contents) {
        return
      }
      if (this.directory.type === 'directory' ) {
        this.isExpanded = !this.isExpanded
      }
    }
  }
}
</script>

<style scoped>
ul, li {
  list-style-type: none;
}
ul.sub-directories > li {
  border-left: 1px solid black;
  padding-left: 10px;
}
li.is-directory > span{
  cursor: pointer;
}
li.is-file > span{
  cursor: default
}
</style>