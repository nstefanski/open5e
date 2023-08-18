<template>
  <section class="docs-container container">
    <h1>{{ plane.name }}</h1>
    <md-viewer :text="plane.desc" />
  </section>
</template>

<script>
import axios from 'axios';
import MdViewer from '~/components/MdViewer';

export default {
  components: {
    MdViewer,
  },
  data() {
    return {
      posts: [],
      errors: [],
      plane: [],
    };
  },
  mounted() {
    return axios
      .get(
        `${useRuntimeConfig().public.apiUrl}/planes/${
          this.$route.params.id
        }`
      ) //you will need to enable CORS to make this work
      .then((response) => {
        this.plane = response.data;
      });
  },
};
</script>

<style lang="scss"></style>
