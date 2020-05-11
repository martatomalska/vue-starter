<template>
    <form @submit.prevent="addNewMeeting()">
        <h3>Dodaj nowe spotkanie</h3>
        <label>Nazwa</label>
        <input type="text" v-model="newMeeting.name">
        <label>Opis</label>
        <textarea v-model="newMeeting.description"></textarea>
        <button>Dodaj</button>
        <span v-if="error" v-bind:class="{redText: error}"> Spotkanie musi mieć nazwę</span>
    </form>
</template>

<script>
    export default {
        data() {
            return {
                newMeeting: {
                    participants: [],
                },
                error: false,
            };
        },
        methods: {
            addNewMeeting() {
                if (!this.newMeeting.name) {
                    this.error = true;
                } else {
                    this.$emit('added', this.newMeeting);
                    this.newMeeting = {};
                    this.error = false;
                }
            }
        }
    }
</script>
<style>
    .redText{
        color: #cf0000;
    }
</style>