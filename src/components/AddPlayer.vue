<template>

<div class="header">
  <form @submit.prevent="submitForm">
  <input v-model="id" placeholder="id" />
  <input v-model="name" placeholder="name" />
  <input v-model="number" placeholder="number" />
  <input v-model="position" placeholder="position" />
  <div><button>Add New Player</button></div>
  </form>
</div>
  
</template>

<script>
export default {
  name: 'AddPlayer',
  data() { 
    return {
        id: '',
        name: '',
        number: '',
        position: '',
    }
  },
  methods: {
    submitForm() {
       this.$emit('newPlayerAdded', this.id, this.name, this.number, this.position);
       this.id = '';
       this.name = '';
       this.number = '';
       this.position = '';
    }
  }
}
</script>

<style scoped>

.header {
  padding: 1rem;
  background-color: #58004d;
  color: white;
  text-align: center;
}

</style>
