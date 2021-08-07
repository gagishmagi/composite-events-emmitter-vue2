<template>
  <div id="app">
    <Search label="name" @search-me="search"/>
    <div>{{state.name}}</div>
  </div>
</template><script>
import Search from "./components/Search";
import { computed, reactive } from "@vue/composition-api";export default {
  name: "App",
  components: {
    Search
  },
  setup() {
    const state = reactive({
      data: {},
      name: computed(() =>
        state.data.name ? `The name is: ${state.data.name} age is: ${state.data.age}` : ""
      )
    });    return {
      state,
      async search(ev) {
        const res = await fetch(`https://api.agify.io/?name=${ev}`);
        state.data = await res.json();
      }
    };
  }
};
</script>