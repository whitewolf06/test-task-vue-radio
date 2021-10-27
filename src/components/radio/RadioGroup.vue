<template>
    <div class="radio-group__wrapper">
      <slot></slot>
    </div>
</template>
<script>

export default {
  name: 'RadioGroup',
  props: ['value','disabled'],
  data() {
      return {
        test: 1
      }
  },
  provide() {
    const rGroup = (() => {
      return {
        value: this.value,
        disabled: this.disabled,
        updateValue: this.updateValue
      }
    })
    return { rGroup }
  },
  methods: {
      updateValue(newValue) {
        this.$emit('input', newValue)
      }
  }
}
</script>
<style lang="scss">
  .radio-group {
    &__wrapper {
      border:1px solid #ccc;
      padding: 10px;
      display: flex;
      flex-wrap: wrap;
    }
  }
</style>