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
            <td>
                <ul>
                    <li v-for="participant in meeting.participants" :key="participant">
                        {{participant}}
                    </li>
                </ul>
            </td>
            <td>
                <button @click = removeMeeting(meeting) style="float: right;margin-left: 15px">Usuń puste spotkanie</button>
                <button @click = addParticipant(meeting) class="button button-outline" style="float: right">Zapisz się</button>
            </td>
        </tr>
        </tbody>
    </table>
</template>

<script>
    export default {
        props: ['meetings'],
        methods: {
            removeMeeting(meeting) {
                this.$emit('remove', meeting);
            },
            addParticipant(meeting){
                this.$emit('addUser', meeting);
            }
        }
    }

</script>