<template>
    <form v-if="adding" @submit.prevent="addNewMeeting()">
        <h3>Dodaj nowe spotkanie</h3>
        <label>Nazwa</label>
        <input type="text" v-model="newMeeting.name">
        <label>Opis</label>
        <textarea v-model="newMeeting.description"></textarea>
        <button>Dodaj</button>
    </form>
    <button @click =displayForm() v-else>Dodaj nowe spotkanie</button>
</template>

<script>
    export default {
        data() {
            return {
                newMeeting: {},
                adding: false
            };
        },
        methods: {
            addNewMeeting() {
                this.$emit('added', this.newMeeting);
                this.newMeeting = {};
                this.adding = false;
            },
            displayForm(){
                this.adding =true;
            }
        }
    }
</script>