<template>
    <table v-if="meetings.length > 0">
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
            <td>{{ meeting.description }}</td>
            <td>
                <ol v-for="participant in meeting.participants">
                    <li>{{ participant }}</li>
                </ol>
            </td>
            <td>
                <div>
                    <button v-if="meeting.participants.indexOf(authenticatedUsername) < 0" @click="subscribe(meeting.name)">Zapisz się</button>
                    <button v-if="meeting.participants.indexOf(authenticatedUsername) >= 0" @click="unsubscribe(meeting.name)">Wypisz się</button>
                    <button v-if="meeting.participants.length == 0" class="button button-outline" @click="remove(meeting.name)">Usuń puste spotkanie</button>
                </div>
            </td>
        </tr>
        </tbody>
    </table>
</template>

<script>
    export default {
        props: ['meetings', 'authenticatedUsername'],
        methods: {
            subscribe(meetingName) {
                this.$emit('subscribe', meetingName);
            },
            unsubscribe(meetingName) {
                this.$emit('unsubscribe', meetingName);
            },
            remove(meetingName) {
                this.$emit('remove', meetingName);
            },

        }
    }
</script>