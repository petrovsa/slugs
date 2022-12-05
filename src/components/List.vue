<template>
  <div>
    filter: <input type="text" v-model="filter" />
    <hr />
    <Ul>
      <li v-for="item in filteredItems" :key="item.id">
        <MyUser :item="item"></MyUser>
      </li>
    </Ul>
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
