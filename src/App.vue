<script>
import FormComponent from '@/components/FormComponent.vue'

export default {
  data() {
    return {
      form: { nombre: 'Felipe', apellido: 'Sanchez', edad: 31 }
    }
  },
  components: {
    FormComponent
  },
  methods: {
    printData(e) {
      this.form = { ...e }
    }
  }
}
</script>

<template>
  <main class="container">
    <div class="output">
      <h3 v-for="(value, key) in form" :key="key">
        {{ key }}: <span>{{ value }}</span>
      </h3>
    </div>
    <FormComponent :data="form" @enviar="printData" />
  </main>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
.output {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: left;
  margin-bottom: 1rem;
  border: 1px solid rgb(2, 3, 80);
  padding: 1rem;
  border-radius: 5px;
  width: 50%;
  background-color: rgb(112, 113, 198);
}
h3 {
  text-transform: capitalize;
  color: #ffffff;
}
span {
  font-weight: bold;
  color: rgb(0, 0, 0);
}
</style>
