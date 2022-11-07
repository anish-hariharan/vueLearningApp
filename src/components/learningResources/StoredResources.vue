<!-- eslint-disable vue/no-mutating-props -->
<template>
  <ul>
    <learning-resources
      v-for="stud in students"
      :key="stud.id"
      :id="stud.id"
      :title="stud.title"
      :description="stud.description"
      :link="stud.link"
      @delete="deleteUser"
    ></learning-resources>
  </ul>
</template>

<script>
import LearningResources from './LearningResources.vue';
export default {
  inject: ['students'],
  components: {
    LearningResources,
  },
  methods: {
    deleteUser(id) {
      const friend = this.students.find((student) => student.id === id);
      let index = this.students.indexOf(friend);
      index === 0 ? this.students.shift() : this.students.splice(index, index);
    },
  },
};
</script>

<style>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
button {
  padding: 0.75rem 1.5rem;
  font-family: inherit;
  background-color: #3a0061;
  border: 1px solid #3a0061;
  color: white;
  cursor: pointer;
}
</style>
