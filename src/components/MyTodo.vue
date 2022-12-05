<template>
  <p>
    <input type="checkbox" :checked="item.completed" />
    {{ item.title }}
  </p>
</template>
<script>
export default {
  name: "MyTodo",
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
};
</script>
