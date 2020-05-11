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
                <ol v-if="meeting.participants.length > 0">
                    <li v-for="(participant, index) in meeting.participants" :key="index">{{ participant }}</li>
                </ol>
            </td>
            <td>
                <button v-if="meeting.participants.indexOf(user) < 1" @click="subscribe(meeting)">Zapisz się</button>
                <button v-if="meeting.participants.indexOf(user) > 0" @click="unsubscribe(meeting)">Wypisz się</button>
                <button v-if="meeting.participants.length < 1" class="button button-outline" @click="remove(meeting)">Usuń puste spotkanie</button>
            </td>
        </tr>
        </tbody>
    </table>
</template>

<script>
    export default {
        props: ['meetings', 'user'],
        methods: {
            subscribe(meeting) {
                this.$emit('subscribe', meeting);
            },
            unsubscribe(meeting) {
                this.$emit('unsubscribe', meeting);
            },
            remove(meeting) {
                this.$emit('remove', meeting);
            }
        }
    }
</script>