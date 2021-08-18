<template>
    <section v-if="video" class="video">
        <div class="video__embed">
            <iframe :src="videoUrl" class="video__embed-item"/>
        </div>
        <div class="video__details">
            <h1>{{ video.snippet.title }}</h1>
            <p>{{ video.snippet.description }}</p>
        </div>
    </section>
</template>

<script>
export default {
    name: 'VideoDetail',
    props: ['video'],
    computed: {
        videoUrl() {
            // const videoId = this.video.id.videoId;
            const { videoId } = this.video.id;
            return `https://www.youtube.com/embed/${videoId}`;
        }
    }
}
</script>

<style scoped>
.video__embed {
    position: relative;
    display: block;
    width: 100%;
    padding: 0;
    overflow: hidden;
    padding-top: 56.25%;
}
.video__embed-item {
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 100%;
    border: 0;
}
.video__details {
    margin: 2rem 0;
}
h1 {
    font-size: 1.5rem;
    line-height: inherit;
    margin-bottom: 1rem;
}
p {
    margin: 0;
}
</style>