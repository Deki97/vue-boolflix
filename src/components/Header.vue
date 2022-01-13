<template>
    <header>
        <div class="container">
            <div class="logo">
                Boolflix
            </div>

            <div class="search">
                <input v-model="userSearch" type="text" placeholder="Cerca un film...">
                <button @click="$emit('filterApi', userSearch)">Cerca</button>
            </div>
        </div>
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
@import '../style/general.scss';

header {
    background-color: black;
    padding: 20px 0;

    .container {
        display: flex;
        justify-content: space-between;
        align-items: center;

        .logo {
        text-transform: uppercase;
        color: red;
        font-size: 30px;
    }

        .search {
            input {
                width: 250px;
                padding: 5px;
            }

            button {
                margin-left: 10px;
                padding: 5px;
            }
        }
    }

    
}
</style>