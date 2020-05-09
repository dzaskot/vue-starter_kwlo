<template>
    <div>
        <h2>
            Witaj: {{ username }}
            <button class="button button-outline" @click="$emit('logout')" style="float: right">Wyloguj</button>
        </h2>
    </div>
</template>

<script>
    export default {
        props: ['username']
    }
</script>