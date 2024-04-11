<template>
  <div>
    <label for="text">Inserte un {{ label }}</label>
    <input
      type="text"
      :name="value"
      :placeholder="placeholder"
      :value="newValue"
      @input="(event) => updateValue(label, event)"
    />
  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: String,
      required: true
    },
    placeholder: {
      type: String,
      default: 'Texto'
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
      this.$emit('changeText', { [key]: this.newInputValue })
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
