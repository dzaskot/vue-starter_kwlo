<template>
    <div>
        <new-meeting-form @added="addNewMeeting($event)"></new-meeting-form>
        <div v-if = "meetings.length !== 0">
            <h3>Zaplanowanie zajęcia ({{meetings.length}})</h3>
            <meetings-list @remove ="removeMeeting($event)" :meetings="meetings"></meetings-list>
        </div>
        <div v-else>
            <p >Brak zaplanowanych spotkań. </p>
        </div>
    </div>
</template>

<script>
    import NewMeetingForm from "./NewMeetingForm";
    import MeetingsList from "./MeetingsList";

    export default {
        components: {NewMeetingForm, MeetingsList},
        data() {
            return {
                meetings: []
            };
        },
        methods: {
            addNewMeeting(meeting) {
                this.meetings.push(meeting);
            },
            removeMeeting(meeting) {
                this.meetings = this.meetings.filter((element)=>element.name !== meeting.name);
            }
        }
    }
</script>>