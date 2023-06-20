<script setup>
import { ref, reactive } from 'vue';
import Header from './components/Header.vue';
import Formulario from './components/Formulario.vue';
import Paciente from './components/Paciente.vue';

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

const guardarPaciente = () => {
    pacientes.value.push({
        ...paciente
    }),

        // Reinicier un objeto
        // paciente.nombre = '',
        // paciente.propretario = '',
        // paciente.email = '',
        // paciente.alta = '',
        // paciente.sintomas = ''

    //segunta forma de reiniciar un objeto
Object.assign(paciente,{
    nombre: '',
    propretario: '',
    email: '',
    alta: '',
    sintomas: ''
})

}
</script>

<template>
    <div class="container mx-auto mt-20">
        <Header />

        <div class="mt-12 md:flex">
            <Formulario v-model:nombre="paciente.nombre" v-model:propretario="paciente.propretario"
                v-model:email="paciente.email" v-model:sintomas="paciente.sintomas" v-model:alta="paciente.alta"
                @guardar-paciente="guardarPaciente" />

            <div class="md:w-1/2 md:h-screen overflow-y-scroll">
                <h3 class="font-black text-3xl text-center">Administra tus pacientes</h3>

                <div v-if="pacientes?.length > 0">
                    <p class="text-lg mt-5 text-center mb-10">
                        Informacion de
                        <span class="text-indigo-600 font-bold">Pacientes</span>
                    </p>

                    <Paciente v-for="paciente in pacientes" :paciente="paciente" />
                </div>
                <p v-else class="mt-10 text-2xl text-center">No hay pacientes</p>
            </div>
        </div>
    </div>
</template>


