<template>
  <ul>
    <li v-for="item in storedResources" :key="item.id"></li>
  </ul>
</template>
<script>
export default {
  data() {
    return {
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
};
</script>