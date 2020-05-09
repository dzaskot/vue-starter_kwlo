<template>
    <form v-if="adding" @submit.prevent="addNewMeeting()">
        <h3>Dodaj nowe spotkanie</h3>
        <label>Nazwa</label>
        <input type="text" v-model="newMeeting.name">
        <label>Opis</label>
        <textarea v-model="newMeeting.description"></textarea>
        <button>Dodaj</button>
        <span v-if="error" style="color: red">{{error}}</span>
    </form>
    <button @click =displayForm() v-else>Dodaj nowe spotkanie</button>
</template>

<script>
    export default {
        data() {
            return {
                newMeeting: {participants: []},
                adding: false,
                error: ''
            };
        },
        methods: {
            addNewMeeting() {
                if(!!this.newMeeting.name) {
                    this.$emit('added', this.newMeeting);
                    this.newMeeting = {};
                    this.adding = false;
                }
                else{
                    this.error = ' Spotkanie musi mieć nazwę!';
                }
            },
            displayForm(){
                this.adding =true;
            }
        }
    }
</script>