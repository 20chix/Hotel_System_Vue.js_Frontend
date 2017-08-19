<template>
  <div class="hello">
  
    <div class="col-lg-3">
      <div class="panel panel-primary">
        <div class="panel-heading">Mub
          <span class="badge pull-right"> 1 </span>
        </div>
        <div class="panel-body">
          <kbd>2</kbd> People
          <kbd> 1</kbd> Kids
          <br>
          <br>
          <kbd>Suit</kbd>
          <button type="button" class="btn btn-danger pull-right" data-toggle="modal" data-target=".bd-example-modal-sm">Delete</button>
        </div>
        <div class="panel-footer">
          <h4>

            <CountdownTimer class="pull left" date="August 22, 2017"></CountdownTimer>
          </h4>
        </div>
      </div>
    </div>


    
  
  </div>
</template>

<script>
import CountdownTimer from './Timer.vue'
export default {
  name: 'hello',
  data() {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  components: {
    CountdownTimer
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
