<template>
  <div>
    <div
      :class="{
        'file-name': true,
        'file-name_active': isActive,
      }"
      @click="handlerActiveFile"
    >
      {{activeElement}}
      <file-icon class="file-icon"/>
      {{ section.name }}
    </div>
  </div>
</template>

<script>
import FileIcon from './FileIcon.vue'

export default {
  name: 'FileItem',
  props: {
    activeElement: {
      type: Array
    },
    section: {
      type: Object
    },
  },
  data: () => ({
    isActive: false
  }),
  components: {
    FileIcon
  },
  methods: {
    handlerActiveFile() {
      this.isActive = !this.isActive
      const a = [this.section.name]
      // this.$emit('update:activeElement', [3333])
      this.$emit('activeChange', a)
    }
  }
}
</script>

<style scoped>
.file-name {
  padding: 5px;
  display: flex;
  align-items: center;
  cursor: pointer;
}
.file-name_active {
  font-weight: bold;
  background: #8fb1c2;
}
.file-name:hover {
  background: #c2c2c2;
}
.file-icon {
  margin-right: 5px;
}
</style>
