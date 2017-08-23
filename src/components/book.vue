<template>
    <div class="container">
        <button class="btn btn-primary pull-right" data-toggle="modal" data-target=".bd-example-modal-lg">Book a room</button>
        <!-- Large modal -->
        <div class="modal fade bd-example-modal-lg" tabindex="-1" role="dialog" aria-labelledby="myLargeModalLabel" aria-hidden="true">
            <div class="modal-dialog modal-lg">
                <div class="modal-content">
                    <div class="modal-header">
                        <button type="button" class="close pull-right" data-dismiss="modal" aria-label="Close">
                            <span aria-hidden="true">&times;</span>
                        </button>
                        <h1 class="modal-title">Book a Room</h1>
                    </div>
                    <div class="modal-body">
    
                        <form>
                            <div class="form-group">
                                <label class="form-control-label" for="formGroupExampleInput">Full Name</label>
    
                                <input type="text" class="form-control" placeholder="e.g. John Smith" v-model="Room.full_name">
                            </div>
                            <div class="form-group">
                                <label class="form-control-label" for="formGroupExampleInput">Checkout</label>
    
                                <input type="text" class="form-control" placeholder="e.g. August 22, 2017" v-model="Room.time">
                            </div>
                            <div class="form-group">
                                <label class="form-control-label" for="formGroupExampleInput">How Many People</label>
    
                                <select class="form-control" id="exampleFormControlSelect1" v-model="Room.people">
                                    <option>1</option>
                                    <option>2</option>
                                    <option>3</option>
                                    <option>4</option>
                                    <option>5</option>
                                </select>
                            </div>
                            <div class="form-group">
                                <label class="form-control-label" for="formGroupExampleInput">How many kids</label>
    
                                <select class="form-control" id="exampleFormControlSelect1" v-model="Room.kids">
                                    <option>0</option>
                                    <option>1</option>
                                    <option>2</option>
                                    <option>3</option>
                                    <option>4</option>
                                    <option>5</option>
                                </select>
                            </div>
                            <div class="form-group">
                                <label class="form-control-label" for="formGroupExampleInput">Room Type</label>
    
                                <input type="text" class="form-control" placeholder="Suit" v-model="Room.room_type">
                            </div>
                            <div class="form-group">
                                <label class="form-control-label" for="formGroupExampleInput">Room Number</label>
    
                                <select class="form-control" id="exampleFormControlSelect1"v-model="Room.room_number">
                                    <option>1</option>
                                    <option>2</option>
                                    <option>3</option>
                                    <option>4</option>
                                    <option>5</option>
                                    <option>6</option>
                                    <option>7</option>
                                    <option>8</option>
                                    <option>9</option>
                                    <option>10</option>
                                </select>
                            </div>
                            <button type="submit" class="btn btn-primary" @click="addToAPI">Book</button>
                        </form>
                    </div>
                    <div class="modal-footer">
    
                    </div>
                </div>
            </div>
        </div>
    
    </div>
</template>

<script>
import axios from 'axios'

export default {
    data() {
        return {

            Room: {
                full_name: '',
                time: '',
                people: '',
                kids: '',
                room_type: '',
                room_number: ''

            }
        }
    },
    methods: {

        addToAPI() {
            let newRoom = {
                full_name: this.Room.full_name,
                time: this.Room.time,
                people: this.Room.people,
                kids: this.Room.kids,
                room_type: this.Room.room_type,
                room_number: this.Room.room_number
            }
            console.log(newRoom);

            axios.post('http://localhost:3000/rooms', newRoom)
                .then((response) => {
                    console.log(response);
      window.location.reload();
                })
                .catch((error) => {
                    consol.log(error);
                })


        }
    }

}
</script>

<style>

</style>
