<script setup>

</script>

<template>
    <div class="md:w-1/2">
        <h2 class="font-black text-3xl text-center"> Seguimiento Pacientes</h2>

        <p class="text-lg mt-5 text-center mb-10">
            Añade Paciente y
            <span class="text-indigo-600 font-bold">Administrarlos</span>
        </p>

        <form class="bg-white shadow-md rounded-lg py-10 px-5 mb-10">

            <div class="mb-5">
                <label for="mascota" class="block text-gray-700 font-bold">
                    Nombre mascota
                </label>
                <input id="mascota" type="text" placeholder="Nombre de la mascota"
                    class="border-2 w-full p-2 mt-1 placeholder-gray-400 rounded-md" />
            </div>

            <div class="mb-5">
                <label for="propretario" class="block text-gray-700 font-bold">
                    Nombre Propretario
                </label>
                <input id="propretario" type="text" placeholder="Nombre del propretrio"
                    class="border-2 w-full p-2 mt-1 placeholder-gray-400 rounded-md" />
            </div>

            <div class="mb-5">
                <label for="email" class="block text-gray-700 font-bold">
                    Email
                </label>
                <input id="email" type="email" placeholder="Email del propretrio"
                    class="border-2 w-full p-2 mt-1 placeholder-gray-400 rounded-md" />
            </div>

            <div class="mb-5">
                <label for="alta" class="block text-gray-700 font-bold">
                    Alta
                </label>
                <input id="alta" type="date" class="border-2 w-full p-2 mt-1 placeholder-gray-400 rounded-md" />
            </div>

            <div class="mb-5">
                <label for="sintomas" class="block text-gray-700 font-bold">
                    Sintomas
                </label>
                <textarea id="sintomas" placeholder="Entra los sintomas del paciente"
                    class="border-2 w-full p-2 mt-1 placeholder-gray-400 rounded-md h-40" />
            </div>

            <input 
            type="submit"
            class="bg-indigo-600 w-full p-3 text-white uppercase font-bold hover:bg-indigo-700 
            cursor-pointer transition-color"
            value="Registrar paciente"
            />

        </form>
    </div>
</template>


