<template>
  <base-card>
    <base-button
      @click="setSelectedTab('stored-resources')"
      :mode="storedResMode"
      >Resource List</base-button
    >
    <base-button @click="setSelectedTab('add-resource')" :mode="addNewResMode"
      >Add new Resource
    </base-button>
  </base-card>
  <component :is="selectedTab"></component>
</template>

<script>
import AddResource from './AddResource.vue';
import StoredResources from './StoredResources';

export default {
  components: {
    AddResource,
    StoredResources,
  },
  computed: {
    storedResMode() {
      return this.selectedTab === 'stored-resources' ? null : 'flat';
    },
    addNewResMode() {
      return this.selectedTab === 'add-resource' ? null : 'flat';
    },
  },
  data() {
    return {
      selectedTab: 'stored-resources',
      storedResources: [
        {
          id: 'R-01',
          title: 'Offical Vue.js Guide',
          description: 'Offical Vue.js Guide documentation',
          link: 'https://vuejs.org',
        },
        {
          id: 'R-02',
          title: 'Google',
          description: 'Learn google!',
          link: 'https://google.com',
        },
      ],
    };
  },
  provide() {
    return {
      resources: this.storedResources,
      addResources: this.addResources,
    };
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addResources(resource) {
      this.storedResources.push({
        id: new Date().toISOString(),
        title: resource.title,
        description: resource.desc,
        link: resource.link,
      });

      this.selectedTab = 'stored-resources';
    },
  },
};
</script>