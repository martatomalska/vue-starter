<template>
    <div>
        <h2>Zajęcia</h2>
        <new-meeting-form @added="addNewMeeting($event)"></new-meeting-form>
        <meetings-list :meetings="meetings" :authenticatedUsername="authenticatedUsername"
                       @subscribe="addParticipant($event)"
                       @unsubscribe="removeParticipant($event)"
                       @remove="removeMeeting($event)"></meetings-list>
    </div>
</template>

<script>
    import NewMeetingForm from "./NewMeetingForm";
    import MeetingsList from "./MeetingsList";

    export default {
        props: ['authenticatedUsername'],
        components: {NewMeetingForm, MeetingsList},
        data() {
            return {
                meetings: [],
                addMeeting: false,
            };
        },
        methods: {
            addNewMeeting(meeting) {
                this.meetings.push(meeting);
                this.addMeeting = false;
            },
            addParticipant(meetingName) {
                for (let i = 0; i < this.meetings.length; i++) {
                    if (this.meetings[i].name == meetingName) {
                        this.meetings[i].participants.push(this.authenticatedUsername);
                    }
                }
            },
            removeParticipant(meetingName) {
                for (let i = 0; i < this.meetings.length; i++) {
                    if (this.meetings[i].name == meetingName) {
                        this.meetings[i].participants.splice(this.meetings[i].participants.indexOf(this.meetings[i]), 1);
                    }
                }
            },
            removeMeeting(meetingName) {
                for (let i = 0; i < this.meetings.length; i++) {
                    if (this.meetings[i].name == meetingName) {
                        this.meetings.splice(i, 1);
                    }
                }
            }
        }
    }
</script>