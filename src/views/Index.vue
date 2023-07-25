<template>
  <div class="container">
    <a-layout>
      <a-layout-header class="header">
        <div class="page-title">
          <router-link to="/">慕课乐高</router-link>
        </div>
        <user-profile :user="user"></user-profile>
      </a-layout-header>
      <a-layout-content class="home-layout">
        <router-view></router-view>
      </a-layout-content>
      <a-layout-footer>
        © 慕课网（imooc.com）版权所有 | 津ICP备20000929号-2
      </a-layout-footer>
    </a-layout>
  </div>
</template>

<script lang='ts'>
  import { defineComponent, computed } from 'vue';
  import { useStore } from 'vuex'
  import { GlobalDataProps } from '../store/index'
  import UserProfile from '../components/UserProfile.vue'
  export default defineComponent({
    setup() {
      const store = useStore<GlobalDataProps>();
      
      const user = computed(() => store.state.user);
      console.log(user);
      return {
        user
      }
    },
    components: {
      UserProfile
    },
  });
</script>

<style scoped >
  .header {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
</style>

