<template>
  <p>{{ item.name }} {{ item.username }}</p>
</template>
<script>
export default {
  name: "MyUser",
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
};
</script>
