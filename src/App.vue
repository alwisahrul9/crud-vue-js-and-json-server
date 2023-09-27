<script setup>
  import Table from './components/Table.vue'
  import Form from './components/Form.vue'
</script>

<template>
  <section class="lg:p-16 p-8">
    <div class="grid grid-cols-12 gap-8">
      <div class="lg:col-span-8 col-span-12">
        <Table />
      </div>
      <div class="lg:col-span-4 col-span-12">
        <Form />
      </div>
    </div>
    
  </section>
</template>

<style scoped>
</style>
