<template>
    <div>
        <h4>Witaj {{username}}</h4>
        <a class="button button-outline" @click="$emit('logout')">Wyloguj</a>
    </div>
</template>

<script>
    export default {
        props: ['username'],
        name: "UserPanel"
    }
</script>

