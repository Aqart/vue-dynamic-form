<template>
  <div v-for="(el, index) in data" :key="index">
    <component
      :is="checkType(typeof el)"
      :value="el"
      :label="index"
      @changeText="handleChange"
      @changeNumber="handleChange"
    />
  </div>
  <button type="submit" @click="onClick">Enviar</button>
</template>

<script>
import InputTextComponent from './InputTextComponent.vue'
import InputNumberComponent from './InputNumberComponent.vue'
export default {
  props: {
    data: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      form: { ...this.data }
    }
  },
  components: {
    InputTextComponent,
    InputNumberComponent
  },
  computed: {},
  methods: {
    handleChange(e) {
      this.form = { ...this.form, ...e }
      return this.form
    },
    checkType(type) {
      if (type === 'string') {
        return 'InputTextComponent'
      } else if (type === 'number') {
        return 'InputNumberComponent'
      } else {
        return 'InputTextComponent'
      }
    },
    onClick() {
      console.log('onClick', this.form)
      this.$emit('enviar', this.form)
    }
  }
}
</script>
<style scoped>
button {
  margin-top: 10px;
  padding: 10px 70px;
}
</style>
