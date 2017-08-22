<template>
  <div class="container">
    <Book></Book>
    <div class="col-lg-3" v-for="room in roomDetails">
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
          <button type="button" class="btn btn-danger pull-right" data-toggle="modal" data-target=".bd-example-modal-sm">Delete</button>
        </div>
        <div class="panel-footer">
          <h4>
            <CountdownTimer :date="room.time"></CountdownTimer>
          </h4>
        </div>
      </div>
    </div>
  
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
      roomDetails: []
    }
  },
  components: {
    CountdownTimer,
    Book
  }, created() {
    axios.get('http://localhost:3000/rooms')
      .then((response) => {
        this.roomDetails = response.data;
        console.log(response);
      })
      .catch((error) => {
        consol.log(error);
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
