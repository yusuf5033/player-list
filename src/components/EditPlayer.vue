<template>

<div id="edit-player-bg">
  <div class="edit-player-container">
    <form @submit.prevent="submitForm">
      <input :value="name" ref="name" placeholder="name" />
      <input :value="number" ref="number" placeholder="number" />
      <input :value="position" ref="position" placeholder="position" />
      <div><button>Save</button><button @click="$emit('editClosed')">Close</button></div>
    </form>
  </div>
</div>
  
</template>

<script>
export default {
  name: 'EditPlayer',
  props: ['id', 'name', 'number', 'position'],
  data() { 
    return {
    }
  },
  methods: {
     submitForm() {
       this.$emit('playerEditSubmitted', this.id, this.$refs.name.value, this.$refs.number.value, this.$refs.position.value);
      
     }
  }
}
</script>
