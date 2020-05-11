<template>
    <div>
        <h4>Witaj {{username}}</h4>
        <a class="button button-outline" @click="$emit('logout')">Wyloguj</a>
    </div>
</template>

<script>
    import MeetingPage from "./meetings/MeetingPage";
    export default {
        components: {MeetingPage},
        props: ['username'],
        name: "UserPanel",
        methods: {
            addNewMeeting(meeting) {
                this.meetings.push("nowe spotkanie")
            }
        },
        data () {
            return {}
        },
    }
</script>

