<template lang=""> 
    <div class="relative overflow-x-auto shadow-md sm:rounded-lg">
        <table class="w-full text-sm text-left text-gray-500 dark:text-gray-400">
            <thead class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">
                <tr>
                    <th scope="col" class="px-6 py-3">
                        No
                    </th>
                    <th scope="col" class="px-6 py-3">
                        Nama
                    </th>
                    <th scope="col" class="px-6 py-3">
                        Kegiatan
                    </th>
                    <th scope="col" class="px-6 py-3">
                        Tindakan
                    </th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(item, index) in data" :key="index" class="bg-white border-b dark:bg-gray-900 dark:border-gray-700">
                    <th scope="row" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white">
                        {{ index+1 }}
                    </th>
                    <td class="px-6 py-4">
                        {{ item.nama }}
                    </td>
                    <td class="px-6 py-4">
                        {{ item.task }}
                    </td>
                    <td class="px-6 py-4 flex gap-4">
                        <ReadModal @read='read(index)' :nama='readData.nama' :task='readData.task'/>
                        <EditModal @edit='edit(index)' :nama='readData.nama' :task='readData.task' :id='readData.id'/>
                        <DeleteBtn @hapus='hapus(index)'/>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>
<script>

import axios from 'axios'

import EditModal from './EditModal.vue'
import ReadModal from './ReadModal.vue'
import DeleteBtn from './DeleteBtn.vue'

export default {
    components: {
        EditModal,
        ReadModal,
        DeleteBtn
    },

    data(){
        return {
            data: [],
            readData: []
        }
    },

    methods: {
        getData(){
            axios.get('http://localhost:3004/data')
        
            .then(response => {
                this.data = response.data
            })
            .catch(error => {
                console.log(error)
            })
        },

        read(n){
            this.readData = this.data[n]
        },

        edit(n){
            this.readData = this.data[n]
        },

        hapus(n){
            this.readData = this.data[n]

            axios.delete(`http://localhost:3004/data/${this.readData.id}`)
            .then(response => {
                console.log(response)
            })
            .catch(error => {
                console.log(error)
            })
        }
    },

    created(){
        this.getData()
    },
    
    updated(){
        this.getData()
    }
}
</script>
<style lang="">
    
</style>