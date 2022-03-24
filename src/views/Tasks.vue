<template>
  <div class="container">
    <div class="but">
      <router-link
        to="/create"
        class="btn btn-success"
        style="background-color: #6610f2"
        >create +</router-link
      >
    </div>

    <div class="row">
      <div class="col-lg-3">
        <card v-for="(p, i) in projects" :key="i" :data="p" />
      </div>
    </div>
  </div>
</template>

<script>
import Card from "../components/Card.vue";
export default {
  components: { Card },

  data() {
    return {
      projects: [],
    };
  },

  mounted() {
    this.get();
  },
  methods: {
    async get() {
      const res = await fetch(
        "https://vue-crud-5bb10-default-rtdb.firebaseio.com/projects.json"
      );
      const data = await res.json();

      for (let i in data) {
        this.projects.push({
          id: i,
          data: data[i],
        });
      }
    },
  },
};
</script>

<style scoped>
.container {
  margin-top: 1rem;
  margin-left: 2rem;
}
.col-lg-3 {
  margin-bottom: 1rem;
}

.but {
  margin-bottom: 1rem;
}

.col-lg-3 {
  margin-bottom: 1rem;
}
</style>
