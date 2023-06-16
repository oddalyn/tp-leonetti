<script>
import { useVuelidate } from "@vuelidate/core";
import { required, email } from "@vuelidate/validators";

export default {
  name: "FormularioWeb",
  setup() {
    return {
      v$: useVuelidate(),
    };
  },
  data() {
    return {
      name: "",
      apellido: "",
      email: "",
      pass: "",
      errors: []
    };
  },
  validations() {
    return {
      name: { required }, // Matches this.firstName
      apellido: { required },
      email: { required, email },
      pass: { required },
    };
  },
  methods: {
    submitHandler: (e) => {
     if(this.v$.name.$error){
        this.errors.push('Debe ingresar un nombre correcto');
        
     }else{
         alert("Formulario enviado");
     }
    },
  },
};
</script>
<template>
  <form @submit.prevent="submitHandler">
    <label for="name">Nombre</label>
    <input type="text" id="name" v-model="name" @blur="v$.name.$touch" />
    <div v-if="v$.name.$error">Debe completar este campo</div>

    <label for="apellido">Apellido</label>
    <input
      type="apellido"
      id="apellido"
      v-model.trim="apellido"
      @blur="v$.apellido.$touch"
    />

    <label for="email">Email</label>
    <input type="text" id="email" v-model.trim="email" @blur="v$.email.$touch" />

    <label for="pass">Constraseña</label>
    <input type="text" id="pass" v-model="pass" @blur="v$.pass.$touch" />

    <button type="submit" @click.capture="enviarFormulario">Enviar</button>
  </form>
</template>
