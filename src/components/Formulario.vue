<script setup>
import { ref, reactive } from "vue"
import Alert from '../components/Alert.vue'

defineEmits([
    'update:nombre',
    'update:propretario',
    'update:email',
    'update:alta',
    'update:sintomas',
])
const props = defineProps({
    nombre: {
        type: String,
        required: true
    },
    propretario: {
        type: String,
        required: true
    },
    email: {
        type: String,
        required: true
    },
    alta: {
        type: String,
        required: true
    },
    sintomas: {
        type: String,
        required: true
    }
})

const alerta = reactive({
    tipo: '',
    mensaje: ''
})

const submit = () => {
    /*
     👉un tipo de validacion posible
    if([paciente.nombre, paciente.propretario].includes("")){
        alert("faltan campos")
    }
    */

    // 👉para no repetir codigo puedo usar Object.values puedo validar todos los campos a la vez
    if (Object.values(props).includes("")) {
        alerta.mensaje = 'Todos los campos son obligatorios'
        alerta.tipo = 'error'
        return
    }
    return (alerta.mensaje = 'Se registro correctamente', alerta.tipo = 'check')

}
</script>

<template>
    <div class="md:w-1/2">
        <h2 class="font-black text-3xl text-center"> Seguimiento Pacientes</h2>

        <p class="text-lg mt-5 text-center mb-10">
            Añade Paciente y
            <span class="text-indigo-600 font-bold">Administrarlos</span>
        </p>

        <Alert v-if="alerta.mensaje" :alerta="alerta" />

        <form class="bg-white shadow-md rounded-lg py-10 px-5 mb-10" @submit.prevent="submit">
            <div class="mb-5">
                <label for="mascota" class="block text-gray-700 font-bold">
                    Nombre mascota
                </label>
                <input id="mascota" type="text" placeholder="Nombre de la mascota" :value="nombre"
                    class="border-2 w-full p-2 mt-1 placeholder-gray-400 rounded-md"
                    @input="$emit('update:nombre', $event.target.value)" />
            </div>

            <div class="mb-5">
                <label for="propretario" class="block text-gray-700 font-bold">
                    Nombre Propretario
                </label>
                <input id="propretario" type="text" placeholder="Nombre del propretrio" :value="propretario"
                    class="border-2 w-full p-2 mt-1 placeholder-gray-400 rounded-md"
                    @input="$emit('update:propretario', $event.target.value)" />
            </div>

            <div class="mb-5">
                <label for="email" class="block text-gray-700 font-bold">
                    Email
                </label>
                <input id="email" type="email" placeholder="Email del propretrio" :value="email"
                    class="border-2 w-full p-2 mt-1 placeholder-gray-400 rounded-md"
                    @input="$emit('update:email', $event.target.value)" />
            </div>

            <div class="mb-5">
                <label for="alta" class="block text-gray-700 font-bold">
                    Alta
                </label>
                <input id="alta" type="date" class="border-2 w-full p-2 mt-1 placeholder-gray-400 rounded-md" :value="alta"
                    @input="$emit('update:alta', $event.target.value)" />
            </div>

            <div class="mb-5">
                <label for="sintomas" class="block text-gray-700 font-bold">
                    Sintomas
                </label>
                <textarea id="sintomas" placeholder="Entra los sintomas del paciente" :value="sintomas"
                    class="border-2 w-full p-2 mt-1 placeholder-gray-400 rounded-md h-40"
                    @input="$emit('update:sintomas', $event.target.value)" />
            </div>

            <input type="submit" class="bg-indigo-600 w-full p-3 text-white uppercase font-bold hover:bg-indigo-700 
            cursor-pointer transition-color" value="Registrar paciente" />

        </form>
    </div>
</template>


