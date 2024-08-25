<template>
    <div class="user elem">
        <button @click="deleteUser(index)">Удалить</button>
        <h3>{{ user.name }}</h3>
        <p>{{ user.email }} — <b>{{ user.pass }}</b></p> <!-- Исправлено с `el.pass` на `user.pass` -->
    </div>
</template>

<script>
export default {
    props: {
        user: {
            type: Object,
            required: true,
        },
        index: {
            type: Number,
            required: true
        },
        deleteUser: {
            type: Function,
            required: true
        }
    }
}
</script>

<style scoped></style>
