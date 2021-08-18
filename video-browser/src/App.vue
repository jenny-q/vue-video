<template>
    <div id="app" class="search container">
        <SearchBar @termChange="onTermChange"></SearchBar>
        <!-- <VideoList v-bind:videos="videos"></VideoList> -->
        <div class="row">
            <div class="col-md-8">
            <VideoDetail :video="selectedVideo" />
            </div>
            <div class="col-md-4">
            <VideoList @videoSelect="onVideoSelect" :videos="videos"></VideoList>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
import VideoDetail from './components/VideoDetail';
const API_KEY = 'AIzaSyCywz8d5Cw4lmh1WrxiuLgC11NnSKNqT3M';
export default {
    name: 'App',
    components: {
        SearchBar,
        VideoList,
        VideoDetail
    },
    data() {
        return { 
            videos: [], selectedVideo: null
        };
    },
    methods: {
        onTermChange(searchTerm) {
            axios.get('https://www.googleapis.com/youtube/v3/search', {
                params: {
                    key: API_KEY,
                    type: 'video',
                    part: 'snippet',
                    q: searchTerm
                }
            }).then(response => {
                this.videos = response.data.items;
            });
        },
        onVideoSelect(video) {
            this.selectedVideo = video;
        }
    }
};
</script>
