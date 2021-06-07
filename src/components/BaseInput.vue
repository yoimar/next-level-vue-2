<template>
  <div>
    <label v-if="label">{{ label }}</label>
    <input 
      :id="label"
      :value="value"
      v-bind="$attrs" 
      v-on="listeners"
      @input="updateValue" />
  </div>
</template>

<script>
import { formFieldMixin } from '../mixins/formFieldMixin'
export default {
  mixins: [formFieldMixin],
  props: {
    value: [String, Number],
    label: String
  },
  computed: {
    listeners() {
      return {
        ...this.$listeners,
        input: this.updateValue
      }
    }
  }
}
</script>
