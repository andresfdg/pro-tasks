<template>
  <div class="container">
    <div class="but">
      <router-link to="/tasks" class="btn btn-primary">back</router-link>
    </div>

    <form @submit.prevent="update">
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

  mounted() {
    this.get();
  },

  methods: {
    async get() {
      const res = await fetch(
        `https://vue-crud-5bb10-default-rtdb.firebaseio.com/projects/${this.id}.json`
      );
      const data = await res.json();
      this.projects = data;
      console.log(this.projects);
    },

    async update() {
      await fetch(
        `https://vue-crud-5bb10-default-rtdb.firebaseio.com/projects/${this.id}.json`,
        {
          method: "PATCH",
          body: JSON.stringify(this.projects),
        }
      );

      window.history.back();
    },
  },
};
</script>
