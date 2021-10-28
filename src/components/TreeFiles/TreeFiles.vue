<template>
  <div>
    <div class="path">{{path}}</div>
    <directory-item
      :section="list"
      @activeChange="activeChange"
    />
  </div>
</template>

<script>
import DirectoryItem from '../DirectoryItem/DirectoryItem.vue'
import {eventBus} from '../../eventBus'

export default {
  name: 'tree',
  props: {
    list: {
      type: Object,
      default: () => {
        return {}
      }
    }
  },
  data: () => ({
    active: [],
  }),
  components: {
    DirectoryItem,
  },
  methods: {
    activeChange(val) {
      this.active = val
      eventBus.$emit('activeChange', val)
    }
  },
  computed: {
    path() {
      const tmp = this.active
      return tmp.reverse().join(' / ')
    }
  }
}
</script>

<style scoped>
.path {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  min-height: 18px;
  padding: 5px;
  border: 1px solid;
  background: #fff;
}
</style>
