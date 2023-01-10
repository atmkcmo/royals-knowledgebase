<template>
    <div>
        <h1>
            {{ player.use_name ? player.use_name : player.first_name }}
            {{ player.last_name }}
        </h1>
        <h2 class="fs-4 d-inline me-3">
            {{ player.club }}
        </h2>
        <TeamRoster @setPlayer="setPlayer" :player="player" :allPlayers="allPlayers"></TeamRoster>
        <h3 class="fs-5">Position: {{ player.position }}</h3>
    </div>
</template>


<script>
import TeamRoster from "./teamRoster.vue";
export default {
    components: { TeamRoster },
    name: "PlayerIdentity",
    props: ["player", 'allPlayers'],
    data() {
        return {

        };
    },
    methods: {
        setPlayer(id) {
            this.$emit("setPlayer", id);
        }
    }
};
</script>
