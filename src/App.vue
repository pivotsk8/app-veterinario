<script setup>
import { ref, reactive } from 'vue';
import Header from './components/Header.vue';
import Formulario from './components/Formulario.vue';

/*👉 para valores unicos se usa mejor ref
const nombre = ref("") */
const pacientes = ref([])

//👉para objetos mejor usar reactive
let paciente = reactive({
    nombre: '',
    propretario: '',
    email: '',
    alta: '',
    sintomas: ''

})
</script>

<template>
    <div class="container mx-auto mt-20">
        <Header />

        <div class="mt-12 md:flex">
            <Formulario 
                v-model:nombre="paciente.nombre"
                v-model:propretario="paciente.propretario"
                v-model:email="paciente.email"
                v-model:sintomas="paciente.sintomas"
                v-model:alta="paciente.alta" />

            <div class="md:w-1/2 md:h-screen overflow-y-scroll">
                <h3 class="font-black text-3xl text-center">Administra tus pacientes</h3>

                <div v-if="pacientes?.length > 0">

                </div>
                <p v-else class="mt-10 text-2xl text-center">No hay pacientes</p>
            </div>
        </div>
    </div>
</template>


