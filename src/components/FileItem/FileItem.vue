<template>
  <div>
    <div
      :class="{
        'file-name': true,
        'file-name_active': isActive,
      }"
      @click="handlerActiveFile"
    >
      <component
        :is="section.type + '-icon'"
        class="file-icon"
      />
      {{ section.name }}
      <span v-if="section.target" class="link-target">({{ section.target }})</span>
    </div>
  </div>
</template>

<script>
import FileIcon from '../Icons/FileIcon.vue'
import LinkIcon from '../Icons/LinkIcon.vue'
import {eventBus} from '../../eventBus'

export default {
  name: 'FileItem',
  props: {
    section: {
      type: Object
    },
  },
  data: () => ({
    isActive: false,
    isClicked: false,
  }),
  created() {
    eventBus.$on('activeChange', () => {
      if(!this.isClicked) this.isActive = false
      this.isClicked = false
    })
  },
  components: {
    FileIcon,
    LinkIcon,
  },
  methods: {
    handlerActiveFile() {
      this.isClicked = this.isActive = true
      this.$emit('activeChange', [this.section.name])
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
.link-target {
  margin-left: 5px;
  font-size: 12px;
  font-style: italic;
}
</style>
