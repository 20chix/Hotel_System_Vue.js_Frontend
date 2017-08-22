<template>
    <div>
    <div v-if="days <= '0' &&  hours <= '0' && minutes <= '0' && seconds <= '0'">
        <p style="color:red;"> 
            0:0:0:0 
        <span class="label label-danger pull-right"> Due </span>
        </p>
    </div>
    <div v-else>
        <p> {{ Math.trunc(days) }}:{{ Math.trunc(hours) }}:{{ Math.trunc(minutes) }}:{{ Math.trunc(seconds) }} 
        <span class="label label-success pull-right">OK</span>
        </p>
    </div>
    </div>
</template>

<script>
export default {

    props: {

        date: {
            type: String

        }

    },
    data() {
        return {
            now: 0,
            count: 0,
        }


    },

    methods: {
        timer_loop() {
            this.count++
            this.now = Math.trunc(new Date().getTime() / 1000)
            //console.log(this.now);
            this.count < 200 && setTimeout(this.timer_loop, 1000)
        },
    },
    mounted() {

        this.timer_loop()
    },
    computed: {
        seconds() {

            return (this.modifiedDate - this.now) % 60

        },

        minutes() {

            return ((this.modifiedDate - this.now) / 60) % 60

        },
        hours() {

            return ((this.modifiedDate - this.now) / 60 / 60) % 24

        },
        days() {

            return ((this.modifiedDate - this.now) / 60 / 60 / 24)

        },
        modifiedDate: function () {
            return Math.trunc(Date.parse(this.date) / 1000)
        }

    }
}
</script>

<style>

</style>
