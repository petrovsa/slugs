<template>
  <div>
    filter: <input type="text" v-model="filter" />
    <hr />
    <ul>
      <li v-for="item in filteredItems" :key="item.id">
        <component :is="itemComponent" :item="item"></component>
        <slot name="item" :item="item"> </slot>
      </li>
    </ul>
  </div>
</template>

<script>
import MyUser from "./MyUser.vue";
export default {
  name: "UserList",
  props: {
    items: {
      type: Array,
      required: true,
    },
    fields: {
      type: Array,
      required: true,
    },
    itemComponent: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      filter: "",
    };
  },
  components: {
    MyUser,
  },
  computed: {
    filteredItems() {
      return this.filter
        ? this.items.filter((u) =>
            this.fields.some((f) =>
              u[f].toLowerCase().includes(this.filter.toLowerCase())
            )
          )
        : this.items;
    },
  },
};
</script>
