<template>
    <div class="radio-item__wrapper" v-bind:class="{_checked: isChecked, _disabled: isDisabled}">
        <div class="radio-item__input" @click="selectItem()">
            <span class="radio-item__control-field"></span>
            <span class="radio-item__control-label">
                <slot />
            </span>
        </div>
    </div>
</template>
<script>
export default {
  name: 'RadioItem',
  props: ['val','value','disabled'],
  inject: {
      rGroup: {
          default: false
      }
  },
  computed: {
      isChecked() {
        return (this.rGroup && this.rGroup().value == this.val) ||
               (!this.rGroup && this.value == this.val)  ? true: false
      },
      isDisabled() {
        return this.rGroup && this.rGroup().disabled || this.disabled ? true: false
      }
  },
  methods: {
      selectItem() {
          if ( !this.isDisabled && this.rGroup ) {
            this.rGroup().updateValue(this.val)
          } else if( !this.isDisabled ) {
              this.$emit('input', this.val)
          }
      }
  },
}
</script>
<style lang="scss">
.radio-item {
    &__wrapper {
        display: flex;
        align-items: center;
        align-content: center;
        margin: 8px 8px;
    }
    &__input {
        display: flex;
        align-items: center;
        cursor: pointer;
    }
    &__wrapper._disabled &__input {
        cursor: default;
    }
    &__control-field {
        display: block;
        background: #fff;
        width: 20px;
        height: 20px;
        border:1px solid #ccc;
        border-radius: 100%;
        position: relative;
        
        &:after {
            content: '';
            width: 50%;
            height: 50%;
            position: absolute;
            left: 25%;
            top: 25%;
            display: block;
            background: teal;
            border-radius: 100%;
            display: none;
        }
        &._disabled {}
    }
    &__wrapper._checked &__control-field {
        &:after {
            display: block;
        }
    }
    &__wrapper._disabled &__control-field {
        border-color: #eaeaea;
        &:after {
            opacity: 0.5;
        }
    }
    &__control-label {
        font-size: 14px;
        color: #555;
        display: block;
        margin: 0 0 0 8px;
    }
    &__wrapper._disabled &__control-label {
        color: #c2c2c2;
    }
}
</style>