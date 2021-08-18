<template>
    <section class="search__bar">
        <!-- <input v-on:input="onInput"/> -->
        <input @input="onInput"/>
    </section>
</template>

<script>
export default {
    name: 'SearchBar',
    methods: { // add events
        onInput: function(event) {
            this.$emit('termChange', event.target.value);
        }
    }
};
</script>

<style scoped>
    input {
        width: 100%;
        padding: .5rem;
    }

    .search__bar {
        text-align: center;
        margin: 20px 0 30px;
    }
</style>