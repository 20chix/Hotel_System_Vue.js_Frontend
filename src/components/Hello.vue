<template>
  <div class="container">
    <Book></Book>
    <br>
    <div class="col-lg-3" v-for="room  in roomDetails">
      <div class="panel panel-primary">
        <div class="panel-heading">{{ room.full_name }}
          <span class="badge pull-right"> {{ room.room_number }} </span>
        </div>
        <div class="panel-body">
          <kbd>{{ room.people }} </kbd> People
          <kbd> {{ room.kids }}</kbd> Kids
          <br>
          <br>
          <kbd>{{ room.room_type }}</kbd>
          <button type="button" class="btn btn-danger pull-right" data-toggle="modal" data-target=".bd-example-modal-sm" @click="DELETE(room, room._id)">Delete</button>
        </div>
        <div class="panel-footer">
          <h4>
            <CountdownTimer :date="room.time"></CountdownTimer>
          </h4>
        </div>
      </div>
    </div>
  
    <div class="modal fade bd-example-modal-sm" id="myModal" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
      <div class="modal-dialog" role="document">
        <div class="modal-content">
          <div class="modal-header">
            <h1 class="modal-title" id="exampleModalLabel">Are you sure?</h1>
            <button type="button" class="close" data-dismiss="modal" aria-label="Close">
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <div class="modal-body">
            Are you sure you want to delete this room? </div>
          <div class="modal-footer">
  
            <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
            <router-link to="/">
              <button type="button" class="btn btn-danger" @click="deleteData(test_room, test_id)">Delete</button>
            </router-link>
          </div>
        </div>
      </div>
    </div>
  
    <!-- @click="deleteData(room, room._id)" -->
  
  </div>
</template>

<script>
import CountdownTimer from './Timer.vue'
import Book from './book.vue'
import axios from 'axios'

export default {
  name: 'hello',
  data() {
    return {
      msg: 'Welcome to Your Vue.js App',
      roomDetails: [],
      test_room: {},
      test_id: ''
    }
  },
  components: {
    CountdownTimer,
    Book,
  },

  methods: {

    DELETE(roomDetails1, id1) {
      $("#my-modal").modal('show');
      this.test_room = roomDetails1;
      this.test_id = id1;

    },
    deleteData(roomDetails, id) {

      axios.delete('http://localhost:3000/rooms/' + id)
        .then(response => this.roomDetails.splice(index, 1));

      window.location.reload();
    }




  }, created() {
    axios.get('http://localhost:3000/rooms')
      .then((response) => {
        this.roomDetails = response.data;
        
        e.log(response);
      })
      .catch((error) => {
        console.log(error);
      })

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
