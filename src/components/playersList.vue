<template>
    <div class="list-width h-100">
        <div class="card mb-2">
            <input type="text" aria-describedby="basic-addon1" class="form-control form-control-lg"
                placeholder="Search for player..." v-model="search" />
        </div>
        <template v-if="loading">
            <Spinner class="mt-5"></Spinner>
        </template>
        <section v-else class="overflow-scroll h-100 wrapper">
            <template v-if="_filteredPlayers.length > 0">
                <div class="list-group">
                    <TransitionGroup name="list" tag="div">
                        <button v-for="(player, index) in _filteredPlayers" :key="index" @click="setPlayer(player.id)"
                            type="button" class="list-group-item list-group-item-action d-flex align-items-center p-1">
                            <img class="img-fluid" width="30" height="45" style="max-width: 30px" :src="player.image"
                                onerror="this.src='https://via.placeholder.com/30x45'" alt="" />
                            <span class="ms-3 fs-6">
                                {{ player.use_name ? player.use_name : player.first_name }}
                                {{ player.last_name }}
                                <span class="text-muted">({{ player.position }})</span>
                            </span>
                        </button>
                    </TransitionGroup>
                </div>
            </template>
            <template v-else>
                <div class="fs-5 text-light px-2">
                    Sorry, no players found with that name.
                </div>
            </template>
        </section>
    </div>
</template>

<script>
import Spinner from "./spinner.vue";
export default {
    name: "PlayersList",
    components: { Spinner },
    props: ["players", "title"],
    data() {
        return {
            loading: true,
            search: ""
        };
    },
    created() {
        if (this._filteredPlayers.length > 0) {
            this.loading = false;
        }
    },
    methods: {
        setPlayer(id) {
            this.$emit("setPlayer", id);
        }
    },

    watch: {
        _filteredPlayers: function (a, b) {
            if (a.length > 0) {
                this.loading = false;
            }
        }
    },
    computed: {
        _filteredPlayers() {
            let search = this.search.toLowerCase();
            return this.players.filter(
                player =>
                    player.first_name.toLocaleLowerCase().includes(search) ||
                    player.use_name.toLocaleLowerCase().includes(search) ||
                    player.last_name.toLocaleLowerCase().includes(search)
            );
        }
    }
};
</script>

<style scoped>
.wrapper {
    height: calc(90vh - 50px) !important;
}

.list-enter-active,
.list-leave-active {
    transition: all 0.5s ease;
}

.list-enter-from,
.list-leave-to {
    opacity: 0;
    transform: translateX(30px);
}

@media (min-width: 1500px) {
    .list-width {
        margin: auto;
    }
}
</style>