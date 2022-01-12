<template>
        <div class="single-serie">
            <div class="title">
                {{ objectSerie.name }}
            </div>

            <div class="original-title">
                {{ objectSerie.original_name }}
            </div>

            <div class="original-language">
                {{ objectSerie.original_language }}
            </div>

            <div class="vote-average">
                {{ objectSerie.vote_average }}
            </div>
        </div>
</template>


<script>

export default {
    name: 'SingleSerie',
    props: {
        objectSerie: Object
    }

}
</script>


<style lang="scss" scoped>
.single-serie {
    margin: 30px 10px;
}
</style>