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
      <div v-for="(sec, ind) of section.contents"
           :key="ind"
           class="tree-item"
      >
        <component
          :is="sec.type + '-item'"
          :section="sec"
          :activeElement.sync="activeElement"
          @activeChange="activeChange"
        />
<!--        -->
<!--        v-on="$listeners""-->
      </div>
    </div>
  </div>
</template>

<script>
import DirectoryItem from './DirectoryItem.vue'
import DirectoryIcon from './DirectoryIcon.vue'
import FileItem from './FileItem.vue'
import LinkItem from './LinkItem.vue'

export default {
  name: 'DirectoryItem',
  props: {
    activeElement: {
      type: Array
    },
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
    LinkItem,
  },
  methods: {
    handlershowDirectory() {
      this.show = !this.show
    },
    activeChange(val) {
      // console.log('section', this.section)
      console.log('val', val)
      let a = val
      a = a.push(123)
      this.$emit('activeChange', [a] )
      // this.$emit('update:activeElement', val)
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
