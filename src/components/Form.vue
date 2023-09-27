<template>
    <form @submit.prevent="save">
        <div class="mb-6">
            <label for="nama" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Nama</label>
            <input type="text" v-model="inputData.nama" id="nama" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="Masukkan Namamu" required>
        </div>
        <div class="mb-6">
            <label for="task" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Kegiatan</label>
            <input type="text" v-model="inputData.task" id="task" placeholder="Rencana Kegiatan" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" required>
        </div>
        <div class="flex justify-end">
            <button type="submit" class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm w-full sm:w-auto px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">Submit</button>
        </div>
    </form>
</template>
<script>

import axios from 'axios'

export default {
    data() {
        return {
            inputData: {
                nama: '',
                task: ''
            }
        }
    },

    methods: {
        save(){
            axios.post('http://localhost:3004/data', this.inputData)

            .then(response => {
                console.log(response)
            })

            .catch(error => {
                console.log(error)
            })

            this.inputData = {
                nama: '',
                task: ''
            }
        }
    }
}
</script>
<style>
    
</style>