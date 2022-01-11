<template>
    <header>
        <input v-model="userSearch" type="text" placeholder="Cerca un film...">
        <button @click="$emit('filterMovies', userSearch)">Cerca</button>
    </header>
</template>


<script>
export default {
    name: 'Header',
    data: function() {
        return {
            userSearch: ''
        }
    }
}
</script>


<style lang="scss" scoped>
header {
    input {
        width: 250px;
        margin: 10px;
    }
}
</style>