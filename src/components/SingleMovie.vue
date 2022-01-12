<template>
        <div class="single-movie">
            <div class="title">
                {{ objectMovie.title }}
            </div>

            <div class="original-title">
                {{ objectMovie.original_title }}
            </div>

            <div class="original-language">
                {{ objectMovie.original_language }}
            </div>

            <div class="vote-average">
                {{ objectMovie.vote_average }}
            </div>
        </div>
</template>


<script>

export default {
    name: 'SingleMovie',
    props: {
        objectMovie: Object
    }

}
</script>


<style lang="scss" scoped>
.single-movie {
    margin: 30px 10px;
}
</style>