<template>
  <div id="app">

    <EditPlayer
    v-if="showEditForm && Object.keys(updatedPlayer).length !== 0"
    @editClosed="showEditForm = false"
    @playerEditSubmitted="updatePlayer"
    :id="updatedPlayer.id"
    :name="updatedPlayer.name"
    :number="updatedPlayer.number"
    :position="updatedPlayer.position">
    </EditPlayer>

   <div class="container">
    
    <AddPlayer @newPlayerAdded="addNewPlayer"></AddPlayer>

    <StudentContent
    v-for="student in student_list"
    @playerDeleted="deletePlayer"
    @editClicked="editClicked"
    :key="student.id"
    :student_data="student">
    </StudentContent>
   </div>
  </div>

</template>

<script>
import StudentContent from './components/StudentContent.vue';
import AddPlayer from './components/AddPlayer.vue'
import EditPlayer from './components/EditPlayer.vue'

export default {
  name: 'App',
  data() {
    return {
      student_list: [
        {
          id: 1,
          name: 'Atiba',
          number: 11,
          position: 'Middle',
        }
      ],
      showEditForm: false,
      updatedPlayer: {}
    }
  },
  methods: {
    updatePlayer(id, name, number, position) {
      var playerToUpdateIndex = this.student_list.findIndex(st_id => st_id.id == id);
      this.student_list[playerToUpdateIndex].name = name;
      this.student_list[playerToUpdateIndex].number = number;
      this.student_list[playerToUpdateIndex].position = position;
      this.showEditForm = false;
    },
    addNewPlayer(id, name, number, position) {
      this.student_list.push({
        id: id,
        name: name,
        number: number,
        position: position
      });
    },
    deletePlayer(id) {
      this.student_list = this.student_list.filter(st_id => st_id.id !== id);
    },
    editClicked(player_id) {
      this.updatedPlayer = this.student_list.find(st_id => st_id.id == player_id);
      this.showEditForm = true;
    }
  },
  components: {
    StudentContent,
    AddPlayer,
    EditPlayer
  }
}
</script>

<style>
* {
  box-sizing: border-box;
}
html {
  font-family: "Jost", sans-serif;
}
body {
  margin: 0;
}

.container {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem auto;
  border-radius: 10px;
  padding: 1rem;
  background-color: #faf8fa;
  width: 50%;
}

#app h2 {
  margin-top: 10px;
  margin-bottom: 10px;
}

input {
  border-color: #fff;
  background-color: #fff;
  padding: 10px;
  width: 48%;
  margin: 1%;
}

#app .row {
  border: 1px solid #ccc;
  color: #58004d;
  border-radius: 5px;
  margin: 10px 0 10px 0;
  padding: 10px;
}
#app button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #ff0077;
  background-color: #ff0077;
  color: white;
  padding: 7px;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
  display: inline-block;
  margin: 5px;
}
#app button:hover,
#app button:active {
  background-color: #ec3169;
  border-color: #ec3169;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}
#edit-player-bg {
  position: fixed; 
  z-index: 1; 
  left: 0;
  top: 0;
  width: 100%; 
  height: 100%; 
  overflow: auto; 
  background-color: rgb(0,0,0); 
  background-color: rgba(0,0,0,0.4);
}
.edit-player-container {
  background-color: #faf8faec;
  margin: 5% auto;
  padding: 40px 20px;
  border: 1px solid #888;
  box-shadow: 0 5px 10px rgba(0, 0, 0, 0.26);
  width: 60%;
}
</style>
