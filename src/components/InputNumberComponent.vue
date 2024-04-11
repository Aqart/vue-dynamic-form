<template>
  <div>
    <label for="number">Inserte un {{ label }}</label>
    <input
      type="number"
      id="number"
      :placeholder="placeholder"
      :name="value"
      :value="newValue"
      @input="(event) => updateValue(label, event)"
    />
  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: Number,
      required: true
    },
    placeholder: {
      type: String,
      default: 'Numero'
    },
    label: {
      type: String,
      required: true
    }
  },
  data() {
    return {
      newInputValue: this.value
    }
  },
  computed: {
    newValue() {
      return this.newInputValue
    }
  },
  methods: {
    updateValue(key, event) {
      this.newInputValue = event.target.value
      this.$emit('changeNumber', { [key]: Number(this.newInputValue) })
    }
  }
}
</script>

<style scoped>
label {
  display: block;
  margin: 1rem 1rem 0.5rem 1rem;
}
input {
  padding: 0.5rem;
  margin: 1rem 1rem 0.5rem 1rem;
}
</style>
