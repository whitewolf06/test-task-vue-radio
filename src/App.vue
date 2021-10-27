<template>
  <div id="app" class="app__wrapper">
    <div class="app__container">
      <h1>Test task</h1>
      <div id="test-block1">
        <h3>(model: radio1, value: {{radio1}}, group disabled)</h3>
        <RadioGroup v-model="radio1" disabled="disabled">
          <RadioItem val="1">Значение 1</RadioItem>
          <RadioItem val="2">Значение 2</RadioItem>
          <RadioItem val="3">Значение 3</RadioItem>
        </RadioGroup>
      </div>
      <div id="test-block2">
        <h3>(model: radio1, value: {{radio1}})</h3>
        <RadioGroup v-model="radio1">
          <RadioItem val="1">Значение 1</RadioItem>
          <RadioItem val="2">Значение 2</RadioItem>
          <RadioItem val="3">Значение 3</RadioItem>
        </RadioGroup>
      </div>
      <div id="test-block3">
        <h3>(model: radio2, value: {{radio2}}), one item disabled</h3>
        <RadioGroup v-model="radio2">
          <RadioItem val="1">Значение 1</RadioItem>
          <RadioItem val="2" disabled="disabled">Значение 2 (disabled)</RadioItem>
          <RadioItem val="3">Значение 3</RadioItem>
          <RadioItem val="4">Значение 4</RadioItem>
        </RadioGroup>
      </div>
      <div id="test-block4">
        <h3>(model: radio2, value: {{radio2}}), one item disabled (not grouped elements)</h3>
        <RadioItem v-model="radio2" val="1">Значение 1</RadioItem>
        <RadioItem v-model="radio2" val="2" disabled="disabled">Значение 2 (disabled)</RadioItem>
        <RadioItem v-model="radio2" val="3">Значение 3</RadioItem>
      </div>
      <div id="test-block5">
        <h3>(model: Countries, value: {{Countries}})</h3>
        <RadioGroup v-model="Countries">
          <RadioItem val="usa">США</RadioItem>
          <RadioItem val="uk">Великобритания</RadioItem>
          <RadioItem val="Ukraine" disabled="disabled">Украина</RadioItem>
          <RadioItem val="RF">Россия</RadioItem>
          <RadioItem val="Fr">Франция</RadioItem>
        </RadioGroup>
      </div>
      <div id="test-block6">
        <h3>(model: Countries, value: {{Countries}}) (not grouped elements)</h3>
        <RadioItem v-model="Countries" val="usa">США</RadioItem>
        <RadioItem v-model="Countries" val="uk">Великобритания</RadioItem>
        <RadioItem v-model="Countries" val="Ukraine" disabled="disabled">Украина</RadioItem>
        <RadioItem v-model="Countries" val="RF" disabled="disabled">Россия</RadioItem>
        <RadioItem v-model="Countries" val="Fr">Франция</RadioItem>
      </div>
    </div>
  </div>
</template>

<script>
import RadioGroup from './components/radio/RadioGroup.vue'
import RadioItem from './components/radio/RadioItem.vue'

export default {
  name: 'App',
  components: {
    RadioGroup,
    RadioItem
  },
  data() {
    return {
      radio1: '2',
      radio2: '',
      Countries: 'uk'
    }
  },
}
</script>

<style lang="scss">
.app {
  &__wrapper {
    width: 100%;
  }
  &__container {
    width: 100%;
    max-width: 1200px;
    margin: 0 auto;
    padding: 20px 20px;
  }
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}
</style>
