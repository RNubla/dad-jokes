<template>
  <form @submit.prevent="OnSubmit">
    <div class="field has-addons">
      <div class="control is-expanded">
        <input
          class="input"
          type="text"
          v-model="text"
          placeholder="Search Jokes"
        />
      </div>
      <div class="control">
        <input class="button is-primary" type="submit" value="Search Jokes" />
      </div>
    </div>
  </form>
</template>

<script>
export default {
  name: "Search",
  data() {
    return {
      text: ""
    };
  },
  methods: {
    OnSubmit() {
      this.$emit("search-text", this.text);
      this.text = "";
    }
  }
};
</script>
