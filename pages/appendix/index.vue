<template>
  <section class="docs-container container">
    <h1>Appendix</h1>
    <div class="docs-toc">
      <ul v-if="appendixSections">
        <li v-for="section in appendixSections" :key="section.slug">
          <nuxt-link tag="a" :to="`/appendix/${section.slug}`">
            {{ section.name }}
          </nuxt-link>
        </li>
      </ul>
    </div>
  </section>
</template>

<script>
import { useMainStore } from '~/store';

export default {
  setup() {
    const store = useMainStore();
    return { store };
  },
  computed: {
    appendixSections: function () {
      return this.store.allAppendixSections;
    },
  },
};
</script>

<style></style>
