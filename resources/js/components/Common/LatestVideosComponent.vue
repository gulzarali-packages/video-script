<style scoped>
.embed-responsive {
    position: relative;
    display: block;
    width: 18%;
    padding: 0;
    overflow: hidden;
    float: left;
    margin: 10px;
}
</style>
<template>
    <div>
        <b-container fluid class="p-4 bg-dark">
            <b-row>
                <b-col>
                    <b-img thumbnail fluid src="https://picsum.photos/250/250/?image=54" alt="Image 1"></b-img>
                </b-col>
                <b-col>
                    <b-img thumbnail fluid src="https://picsum.photos/250/250/?image=58" alt="Image 2"></b-img>
                </b-col>
                <b-col>
                    <b-img thumbnail fluid src="https://picsum.photos/250/250/?image=59" alt="Image 3"></b-img>
                </b-col>

            </b-row>
        </b-container>
        <b-container fluid class="p-4">
            <b-row>
                <b-col>
                    <div v-for="video in videos" v-bind:key="video.id.videoId">
                        <b-embed type="iframe" aspect="16by9" v-bind:src="'https://www.youtube.com/embed/'+video.id.videoId+'?rel=0'"
                            allowfullscreen></b-embed>
                    </div>

                    <!-- <p>{{ video.id.videoId }}</p> -->

                </b-col>
            </b-row>
        </b-container>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                videos: [],
            };
        },
        methods: {
            async fetchVideos() {
                try {
                    const response = await this.$http.get(
                        "https://www.googleapis.com/youtube/v3/search?type=video&maxResults=10&q=hot&key="
                    );
                    console.log(response.data.items);
                    this.videos = response.data.items;
                } catch (error) {
                    console.log(error);
                }
            }
        },
        created() {
            this.$root.$refs.fetch_youtube_videos = this;
        }
    }
</script>