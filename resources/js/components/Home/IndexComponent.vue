<template>
    <div>
        <TopNavBar></TopNavBar>
        <LatestVideos></LatestVideos>
    </div>

</template>

<script>
    import TopNavBar from '../Common/TopNavBarComponent';
    import LatestVideos from '../Common/LatestVideosComponent.vue';
    export default {
        mounted() {
            console.log('Component mounted.')
        },
        components: {
            TopNavBar,
            LatestVideos
        }
    }
</script>