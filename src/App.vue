<template>
  <div
    id="app"
    class="app"
  >
    <app-header />

    <div class="app__content">
      <router-view/>
    </div>
  </div>
</template>

<script>
import AppHeader from '@/components/App/AppHeader';

export default {
  components: {
    AppHeader,
  },
};
</script>

<style lang="scss" src="./styles/main.scss"></style>
