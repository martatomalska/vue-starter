<template>
    <div>
        <h3>Witaj {{username}}</h3>
        <a class="button button-outline" @click="$emit('logout')">Wyloguj</a>
    </div>
</template>

<script>
    export default {
        props: ['username'],
        name: "UserPanel"
    }
</script>

