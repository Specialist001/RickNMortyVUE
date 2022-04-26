<template>
    <div>
        <character-block :character="character"/>
        <button @click="goBack"> Go Back </button>
    </div>
</template>

<script>
    import CharacterBlock from "@/components/CharacterBlock";
    export default {
        name: "rick-character",
        components: {
            CharacterBlock
        },
        data() {
            return {
                character: null,
            }
        },
        async created() {
            const {id} = this.$route.params.id;
            if (id) {
                this.character = await this.$store.dispatch('fetchSingleCharacter', id)
            }
        },
        methods: {
            goBack() {
                this.$router.push({name: 'RickList'})
            }
        }
    }
</script>

<style scoped>

</style>