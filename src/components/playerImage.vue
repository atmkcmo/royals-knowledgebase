<template>
    <img class="player-image img-fluid" :src="player.image" onerror="this.src='https://via.placeholder.com/223x330'"
        alt="" />
</template>

<script>
export default {
    name: "PlayerImage",
    props: ["player"],
};
</script>

<style scoped>
.player-image {
    border: 2px solid #ddd;
    /* border: 2px solid #004687; */
}
</style>
