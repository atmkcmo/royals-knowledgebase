<template>
    <div class="row g-0 h-100">
        <div class="col-md-3 bg-primary h-100 p-3 p-lg-5 border-right">
            <div class="h-100 player-list-wrapper-">
                <PlayersList @setPlayer="setPlayer" :players="allPlayers" title="All Players"></PlayersList>
            </div>
        </div>
        <div class="col-md-9 h-100 p-3 p-lg-5">
            <div class="h-100">
                <div v-if="_playerSet" class="card h-100 player-card p-2 text-start">
                    <div class="card-body overflow-scroll">
                        <PlayerInfo @setPlayer="setPlayer" :player="player" :allPlayers="allPlayers"></PlayerInfo>
                        <PlayerStats :player="player" class="my-3"></PlayerStats>
                        <PlayerReports :player="player"></PlayerReports>
                        <div id="page-bottom"></div>
                    </div>
                </div>
                <div v-else class="h-100 d-flex flex-column justify-content-center align-items-center">
                    <img src="./assets/images/royals-logo.png" alt="" />
                    <h1 class="text-light"><i>Roster Knowledge Base</i></h1>
                    <h3>Please select player from list...</h3>
                </div>
            </div>
        </div>
    </div>
</template>


<script>
import PlayersList from "./components/playersList.vue";
import PlayerInfo from "./components/playerInfo.vue";
import PlayerStats from "./components/playerStats.vue";
import PlayerReports from "./components/playerReports.vue";
import Spinner from "./components/spinner.vue";
import axios from "axios";

export default {
    name: "Home",
    components: {
        PlayersList,
        PlayerStats,
        PlayerInfo,
        PlayerReports,
        Spinner
    },
    data() {
        return {
            allPlayers: [],
            allTeams: [],
            loading: true,
            player: {},
            centerAll: "justify-content-center align-items-center"
        };
    },
    mounted() {
        this.fetchData();
    },
    computed: {
        _playerSet() {
            return Object.keys(this.player).length === 0 ? false : true;
        }
    },
    methods: {
        async fetchData() {
            let that = this;
            this.loading = true;
            this.allProducts = [];
            const baseURI = "/players.json";
            await axios.get(baseURI).then(result => {
                that.allPlayers.push(...result.data);
            });
            that.allPlayers.sort((a, b) =>
                a.last_name > b.last_name ? 1 : b.last_name > a.last_name ? -1 : 0
            );
            that.loading = false;
        },
        setPlayer(id) {
            this.player = [];
            let a = this.allPlayers.find(player => player.id == id);
            this.player = a;
        }
    }
};
</script>

<style scoped>
.player-card {
    border: 3px solid #bd9b60;
    max-width: 1200px;
    margin: auto;
    height: 90vh;
}

.player-list-wrapper {
    overflow: scroll;
}

.border-right {
    border-right: 0px solid #bd9b60;
}

main {
    padding: 32px 0;
}

nav {
    box-shadow: 0 0 8px 2px #888;
}

@media (min-width: 1024px) {}
</style>
