<template>
    <section>
        <div class="row">
            <div class="col-xl-3">
                <PlayerImage :player="player"></PlayerImage>
            </div>
            <div class="col-xl-5">
                <div class="d-flex h-100 flex-column justify-content-center">
                    <PlayerIdentity @setPlayer="setPlayer" :player="player" :allPlayers="allPlayers"></PlayerIdentity>
                    <PlayerBio :player="player"></PlayerBio>
                </div>
            </div>
            <div class="col-xl-4 offset-xl-0 ps-lg-5">
                <PlayerSchedule :player="player"></PlayerSchedule>
            </div>
        </div>
        <div class="row">
            <div class="col">
                <PlayerCharacteristics class="mt-3" :player="player"></PlayerCharacteristics>
            </div>
        </div>
    </section>
</template>


<script>
import PlayerImage from "./playerImage.vue";
import PlayerIdentity from "./playerIdentity.vue";
import PlayerBio from "./playerBio.vue";
import PlayerCharacteristics from "./playerCharacteristics.vue";
import PlayerSchedule from "./playerSchedule.vue";
export default {
    name: "PlayerInfo",
    components: {
        PlayerSchedule,
        PlayerImage,
        PlayerIdentity,
        PlayerBio,
        PlayerCharacteristics
    },
    props: ["player", "allPlayers"],
    data() {
        return {};
    },
    methods: {
        setPlayer(id) {
            this.$emit("setPlayer", id);
        }
    }
};
</script>

<style scoped>
@media (min-width: 1024px) {}
</style>
