<template>
  <li>
    <span>{{ node.title }}: {{node.name}}</span>
  </li>
  <ul v-if="hasChildren">
    <li><EmployeeTree v-for="child in node.children" :key="child.id" :node="child" /></li>
  </ul>
</template>

<script>
export default {
  name: "EmployeeTree",
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