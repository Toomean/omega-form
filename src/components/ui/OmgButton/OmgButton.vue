<template>
  <button
    class="omg-button"

    v-bind="$attrs"

    @click="onClick"
  >
    <slot />
  </button>
</template>

<script>
export default {
  name: 'OmgButton',

  inheritAttrs: false,

  methods: {
    onClick(event) {
      this.$emit('click', event);
    },
  },
};
</script>

<style lang="scss" src="./OmgButton.scss"></style>
