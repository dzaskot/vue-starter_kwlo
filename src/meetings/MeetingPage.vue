<template>
    <div>
        <new-meeting-form @added="addNewMeeting($event)" :meetings="meetings"></new-meeting-form>
        <div v-if = "meetings.length !== 0">
            <h3>Zaplanowanie zajęcia ({{meetings.length}})</h3>
            <meetings-list @addUser="addParticipant($event)" @removeMeeting ="removeMeeting($event)" @removeParticipant ="removeParticipant($event)"
                           :meetings="meetings" :username="username"></meetings-list>
        </div>
        <div v-else>
            <p >Brak zaplanowanych spotkań.</p>
        </div>
    </div>
</template>

<script>
    import NewMeetingForm from "./NewMeetingForm";
    import MeetingsList from "./MeetingsList";

    export default {
        props: ['username'],
        components: {NewMeetingForm, MeetingsList},
        data() {
            return {
                meetings: [],
            };
        },
        methods: {
            addNewMeeting(meeting) {
                this.meetings.push({...meeting, participants: []});
            },
            removeMeeting(meeting) {
                this.meetings = this.meetings.filter((element)=>element.name !== meeting.name);
            },
            addParticipant(meeting){
                this.meetings.find((element) =>
                    element.name === meeting.name).participants.push(this.username);
            },
            removeParticipant(meeting){
                const m = this.meetings.find(element => element.name === meeting.name);
                m.participants = m.participants.filter(element =>element !== this.username);

            }
        }
    }
</script>>