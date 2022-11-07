<template>
  <base-card>
    <base-button @click="setSelectedTab('stored-resources')"
      >Stored Resources</base-button
    >
    <base-button @click="setSelectedTab('add-resource')"
      >Add Resource</base-button
    >
  </base-card>
  <component :is="selectedTab"></component>
</template>

<script>
import StoredResources from './StoredResources.vue';
import AddResource from './AddResource.vue';

export default {
  components: {
    StoredResources,
    AddResource,
  },
  data() {
    return {
      selectedTab: 'stored-resources',
      students: [
        {
          id: 'offline-guide',
          title: 'Offline Guide',
          description: 'The official Vue.js documentation',
          link: 'https://vuejs.org/',
        },
        {
          id: 'google',
          title: 'Google',
          description: 'Learn to google',
          link: 'https://google.org',
        },
      ],
    };
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
      console.log(tab);
    },
    addResources(title, description, link) {
      const newResource = {
        id: new Date().toISOString(),
        title: title,
        description: description,
        link: link,
      };
      this.students.push(newResource);
      console.log(newResource.url);
      this.selectedTab = 'stored-resources';
    },
  },
  provide() {
    return {
      students: this.students,
      addResources: this.addResources,
    };
  },
};
</script>
