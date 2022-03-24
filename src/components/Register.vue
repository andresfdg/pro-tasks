<template>
  <form @submit.prevent="validation">
    <div class="mb-3">
      <label for="exampleInputEmail1" class="form-label">Email address</label>
      <input
        v-model="mail"
        type="email"
        class="form-control"
        id="exampleInputEmail1"
        aria-describedby="emailHelp"
      />
    </div>
    <div class="mb-3">
      <label for="exampleInputPassword1" class="form-label">Password</label>
      <input
        v-model="pas1"
        type="password"
        class="form-control"
        id="exampleInputPassword1"
      />
    </div>
    <div class="mb-3">
      <label for="exampleInputPassword2" class="form-label"
        >Confirm Password</label
      >
      <input
        v-model="pas2"
        type="password"
        class="form-control"
        id="exampleInputPassword2"
      />
    </div>

    <button type="submit" class="btn btn-primary">Register</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      mail: "",
      pas1: "",
      pas2: "",
    };
  },
};
</script>

<style></style>
