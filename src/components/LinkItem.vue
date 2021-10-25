<template>
  <div>
    <div class="link-name">
      <link-icon class="link-icon"/>
      {{ section.name }}
      <span class="link-target">({{ section.target }})</span>
    </div>
  </div>
</template>

<script>
import LinkIcon from './LinkIcon.vue'

export default {
  name: 'LinkItem',
  props: {
    section: {
      type: Object,
    },
  },
  components: {
    LinkIcon
  }
}
</script>

<style scoped>
.link-name {
  padding: 5px;
  display: flex;
  align-items: center;
  cursor: pointer;
}

.link-name:hover {
  background: #c2c2c2;
}

.link-icon {
  margin-right: 5px;
}

.link-target {
  margin-left: 5px;
  font-size: 12px;
  font-style: italic;
}
</style>
