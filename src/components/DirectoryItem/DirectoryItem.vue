<template>
  <div>
    <div class="directory">
      <div
        @click="handlershowDirectory"
        class="directory-name"
      >
        <directory-icon class="directory-icon"/>
        {{ section.name }}
      </div>
    </div>
    <div v-if="show">
      <div
        v-for="(sec, ind) of section.contents"
        :key="ind"
        class="tree-item"
      >
        <component
          :is="(sec.type === 'link' ? 'file' : sec.type) + '-item'"
          :section="sec"
          @activeChange="activeChange"
        />
      </div>
    </div>
  </div>
</template>

<script>
import DirectoryItem from './DirectoryItem.vue'
import DirectoryIcon from '../Icons/DirectoryIcon.vue'
import FileItem from '../FileItem/FileItem.vue'

export default {
  name: 'DirectoryItem',
  props: {
    section: {
      type: Object
    },
  },
  data: () => ({
    show: false,
  }),
  components: {
    DirectoryItem,
    DirectoryIcon,
    FileItem,
  },
  methods: {
    handlershowDirectory() {
      this.show = !this.show
      this.$emit('activeChange', [this.section.name])
    },
    activeChange(val) {
      val.push(this.section.name)
      this.$emit('activeChange', val)
    }
  }
}
</script>

<style scoped>
.directory {
  background: #e8e8e8;
  border-left: 2px solid;
  margin-top: 5px;
}

.directory-name {
  padding: 5px;
  display: flex;
  align-items: center;
  cursor: pointer;
}

.directory-name:hover {
  background: #c2c2c2;
}

.directory-icon {
  margin-right: 5px;
}

.tree-item {
  margin-left: 20px;
}
</style>
