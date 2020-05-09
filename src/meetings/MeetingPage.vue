<template>
    <div>
        <new-meeting-form @added="addNewMeeting($event)"></new-meeting-form>
        <h3>Zaplanowanie zajęcia ({{meetings.length}})</h3>
        <meetings-list :meetings="meetings"></meetings-list>
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
            }
        }
    }
</script>>