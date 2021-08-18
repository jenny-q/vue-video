<template>
    <li class="list-group-item" @click="onVideoSelect">
        <!-- <img :src="video.snippet.thumbnails.default.url" alt="" />  -->
        <img :src="thumbnailUrl" alt="" />
        <div class="list-group-item__text">
            {{ video.snippet.title }}
        </div>  
    </li>
</template>

<script>
export default {
    name: 'VideoListItem',
    props: ['video'],
    computed: {
        thumbnailUrl() {
            return this.video.snippet.thumbnails.default.url;
        }
    },
    methods: {
        onVideoSelect() {
            this.$emit('videoSelect', this.video);
        }
    }
};
</script>

<style scoped>
    .list-group-item {
        display: flex;
        cursor: pointer;
    }
    .list-group-item:hover {
        background: #eee;
    }
    .list-group-item__text {
        margin-left: 1rem;
        font-size: .85rem;
    }
</style>
