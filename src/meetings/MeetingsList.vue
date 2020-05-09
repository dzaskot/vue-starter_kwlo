<template>
    <table>
        <thead>
        <tr>
            <th>Nazwa spotkania</th>
            <th>Opis</th>
            <th>Uczestnicy</th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="meeting in meetings" :key="meeting.name">
            <td>{{ meeting.name }}</td>
            <td>{{ meeting.description}}</td>
            <td>{{ meeting.participants}}</td>
        </tr>
        </tbody>
    </table>
</template>

<script>
    export default {
        props: ['meetings']
    }
</script>