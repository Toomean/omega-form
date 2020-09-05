<template>
  <label
    class="form-input"
  >
    <input
      :class="{
        '--has-value': !!value,
        '--has-error': !!error,
      }"
      v-bind="$attrs"
      @input="onInput"
    />
    <span
      v-if="inputLabel"
      class="form-input__label"
    >
      {{ inputLabel }}
    </span>
  </label>
</template>

<script>

export default {
  inheritAttrs: false,

  props: {
    label: {
      type: String,
      default: '',
    },
    error: {
      type: String,
      default: '',
    },
    mask: {
      type: String,
      default: '',
    },
    value: {
      type: [String, Number],
      default: '',
    },
  },

  computed: {
    inputLabel() {
      return this.label || this.$attrs.placeholder;
    },
  },

  methods: {
    onInput(event) {
      this.$emit('input', event.target.value);
    },
  },
};
</script>

<style lang="scss" src="./FormInput.scss"></style>
