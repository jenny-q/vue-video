<template>
    <section>
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

<style>

</style>