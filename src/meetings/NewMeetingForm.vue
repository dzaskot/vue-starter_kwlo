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
        props: ['meetings'],
        data() {
            return {
                newMeeting: {},
                adding: false,
                error: ''
            };
        },
        methods: {
            addNewMeeting() {
                if(!!this.newMeeting.name){
                    if(this.meetings.find((element)=>element.name === this.newMeeting.name)){
                        this.error = ' Spotkanie musi mieć unikalną nazwę!';
                    }
                    else {
                        this.$emit('added', this.newMeeting);
                        this.newMeeting = {};
                        this.adding = false;
                        this.error = '';
                    }
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