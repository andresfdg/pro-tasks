<template>
  <div class="container">
    <div>
      <router-link to="/tasks" class="btn btn-primary">back</router-link>
    </div>

    <form @submit.prevent="push">
      <div class="mb-3">
        <label for="formGroupExampleInput" class="form-label">title</label>
        <input
          type="text"
          class="form-control"
          id="formGroupExampleInput"
          placeholder="insert title"
          v-model="projects.title"
        />
      </div>
      <div class="mb-3">
        <label for="formGroupExampleInput2" class="form-label"
          >description</label
        >
        <textarea
          class="form-control"
          id="validationTextarea"
          placeholder="insert dscription"
          required
          v-model="projects.description"
        ></textarea>
      </div>

      <div class="send">
        <input type="submit" class="btn btn-primary" value="send" />
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      projects: {},
      id: this.$route.params.id,
    };
  },

  methods: {
    async push() {
      await fetch(
        "https://vue-crud-5bb10-default-rtdb.firebaseio.com/projects.json",
        {
          method: "POST",
          body: JSON.stringify(this.projects),
        }
      );

      window.history.back();
    },
  },
};
</script>
