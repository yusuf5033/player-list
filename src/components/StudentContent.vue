<template>
  <div class="row">
    <h2 class="name title">{{ student_data.name }}</h2>
    <div class="details">
      <div class="number">Number: {{ student_data.number }}</div>
      <div class="position">Position: {{ student_data.position }}</div>
    </div>

    <div class="actions">
      <button @click="$emit('editClicked', student_data.id)">Edit</button>
      <button @click="$emit('playerDeleted', student_data.id)">Delete</button>
    </div>

  </div>
</template>

<script>
export default {
  name: 'StudentContent',
  props: {
    student_data: Object
  }
}
</script>

<style scoped>
</style>
