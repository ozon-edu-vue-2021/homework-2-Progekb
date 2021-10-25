<template>
  <div>
    {{active}}
    <directory-item
      :section="require('../../public/static/node_modules.json')"
      :activeElement.sync="active"
      @activeChange="activeChange"
    />
  </div>
</template>

<script>
import DirectoryItem from './DirectoryItem.vue'

export default {
  name: 'tree',
  props: {},
  data: () => ({
    active: [],
  }),
  components: {
    DirectoryItem,
  },
  methods: {
    activeChange(val) {
      this.active = val
    }
  }
}
</script>

<style scoped>

</style>
