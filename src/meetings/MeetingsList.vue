<template>
    <table>
        <thead>
        <tr>
            <th>Nazwa spotkania</th>
            <th>Opis</th>
            <th>Uczestnicy</th>
            <th></th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="meeting in meetings" :key="meeting.name">
            <td>{{ meeting.name }}</td>
            <td>{{ meeting.description}}</td>
            <td>{{ meeting.participants}}</td>
            <td>
                <button @click = removeMeeting(meeting) style="float: right;margin-left: 15px">Usuń puste spotkanie</button>
                <button @click = addParticipant() class="button button-outline" style="float: right">Zapisz się</button>
            </td>
        </tr>
        </tbody>
    </table>
</template>

<script>
    export default {
        props: ['meetings','username'],
        methods: {
            removeMeeting(meeting) {
                this.$emit('remove', meeting);
            },
            addParticipant(){

            }
        }
    }

</script>