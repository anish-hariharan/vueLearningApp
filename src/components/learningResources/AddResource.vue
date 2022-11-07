<template>
  <base-dialog
    v-if="inputIsInvalid"
    title="Invalid Input"
    @close="confirmError"
  >
    <template #default>
      <p>input is invalid</p>
      <p>please check values before enter</p>
    </template>
    <template #actions>
      <base-button @click="confirmError">Okay</base-button>
    </template>
  </base-dialog>
  <base-card>
    <form @submit.prevent="submitData">
      <div class="form-control">
        <label for="title">Title</label>
        <input ref="titleInput" type="" name="title" id="title" />
      </div>
      <div class="form-control">
        <label for="description">description</label>
        <textarea
          ref="descri"
          name="description"
          id="description"
          rows="3"
        ></textarea>
      </div>
      <div class="form-control">
        <label for="link">link</label>
        <input ref="url" type="url" name="link" id="link" />
      </div>
      <div>
        <base-button type="submit"> Add Resource </base-button>
      </div>
    </form>
  </base-card>
</template>

<script>
export default {
  inject: ['addResources'],
  data() {
    return {
      inputIsInvalid: false,
    };
  },
  methods: {
    submitData() {
      console.log('running');
      const dTitle = this.$refs.titleInput.value;
      const dDescri = this.$refs.descri.value;
      const dLink = this.$refs.url.value;
      if (dTitle.length === 0 || dDescri.length === 0 || dLink.length === 0) {
        this.inputIsInvalid = true;
      } else {
        this.addResources(dTitle, dDescri, dLink);
      }
    },
    confirmError() {
      this.inputIsInvalid = false;
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
