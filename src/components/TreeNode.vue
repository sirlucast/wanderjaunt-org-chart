<template>
  <li>
    {{ node.name }}
  </li>
  <ul v-if="hasChildren">
    <li><TreeNode v-for="child in node.children" :key="child.id" :node="child" /></li>
  </ul>
</template>

<script>
export default {
  name: "TreeNode",
  props: {
    node: {
      type: Object,
      required: true,
    },
  },
  computed: {
    hasChildren() {
      const { children } = this.node;
      return children && children.length > 0;
    },
  },
};
</script>