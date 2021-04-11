<template >
  <base-card>
    <h2>Add new resource</h2>

    <form @submit.prevent>
      <div class="form-control">
        <label for="title">Title</label>
        <input type="text" ref="title" name="title" />
      </div>

      <div class="form-control">
        <label for="description">Description</label>
        <textarea type="text" ref="description" name="description" />
      </div>

      <div class="form-control">
        <label for="link">Link</label>
        <input rows="3" type="text" ref="link" name="link" />
      </div>
      <base-button @click="submitData" type="submit"> Add Resource</base-button>
    </form>
  </base-card>
</template>

<script>
export default {
  inject: ['addResources'],
  methods: {
    submitData() {
      const formData = {
        title: this.$refs.title.value,
        desc: this.$refs.description.value,
        link: this.$refs.link.value,
      };
      this.addResources(formData);
    },
  },
};
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>