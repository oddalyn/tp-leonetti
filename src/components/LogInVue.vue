<script>


</script>
<template>
    <form @submit.prevent="submitHandler">
        <label for="email">Email</label>
        <input type="text" id="email" v-model="email">

        <label for="pass">Contraseña</label>
        <input type="text" id="pass" v-model="pass">

        <div class="container">
            <button>Enviar</button>
        </div>
    </form>
</template>