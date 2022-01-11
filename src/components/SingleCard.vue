<template>
        <div class="single-card">
            <div class="title">
                {{ objectCard.title }}
            </div>

            <div class="original-title">
                {{ objectCard.original_title }}
            </div>

            <div class="original-language">
                {{ objectCard.original_language }}
            </div>

            <div class="vote-average">
                {{ objectCard.vote_average }}
            </div>
        </div>
</template>


<script>

export default {
    name: 'SingleCard',
    props: {
        objectCard: Object
    }

}
</script>


<style lang="scss" scoped>

</style>