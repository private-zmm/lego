<template>
  <div class="container">
    <a-row :gutter="16">
      <template-list :list="testData"></template-list>
    </a-row>
   
  </div>
</template>

<script lang='ts'>
  import { computed, defineComponent } from 'vue';
  import { useStore } from 'vuex';
  import TemplateList from '../components/TemplateList.vue';
  import { GlobalDataProps } from '../store/index';
  export default defineComponent({
    name: 'home',
    components: {
      TemplateList,
    },
    setup() {
      const store = useStore<GlobalDataProps>();
      const testData = computed(() => store.state.templates.data);
      return {
        testData,
      };
    },
  });
</script>

<style scoped >
  .container {
    background: #fff;
    padding: 0 24px 24px 30px;
    min-height: 85vh;
    max-width: 1200px;
    margin: 50px auto;
    width: 100%;
  }
</style>
