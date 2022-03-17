<template>
  <div class="card" style="width: 18rem">
    <div class="card-body">
      <h5 class="card-title">{{ data.data.title }}</h5>
      <p class="card-text">{{ data.data.description }}</p>
      <div class="row">
        <router-link
          :to="`/edit/${data.id}`"
          class="col-6 btn btn-primary"
          style="background-color: ##6610f2"
          >edit</router-link
        >
        <button
          @click="deletee"
          class="col-6 btn btn-primary"
          style="background-color: #f00524"
        >
          delete
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    data: {},
  },

  methods: {
    async deletee() {
      const id = this.data.id;
      const res = await fetch(
        `https://vue-crud-5bb10-default-rtdb.firebaseio.com/projects/${id}.json`,
        {
          method: "DELETE",
        }
      );
      location.reload();
    },
  },
};
</script>
