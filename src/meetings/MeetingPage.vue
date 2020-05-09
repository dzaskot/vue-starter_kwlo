<template>
    <div>
        <new-meeting-form @added="addNewMeeting($event)"></new-meeting-form>
        <div v-if = "meetings.length !== 0">
            <h3>Zaplanowanie zajęcia ({{meetings.length}})</h3>
            <meetings-list @addUser="addParticipant($event)" @remove ="removeMeeting($event)" :meetings="meetings"></meetings-list>
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
            }
        }
    }
</script>>