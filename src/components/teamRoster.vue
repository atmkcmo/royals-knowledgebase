<template>
    <div class="d-inline">
        <button class="btn btn-light btn-sm text-light bg-secondary" type="button" data-bs-toggle="offcanvas" data-bs-target="#offcanvasRight"
            aria-controls="offcanvasRight">
            View Team Roster
        </button>

        <div class="offcanvas offcanvas-end" tabindex="-1" id="offcanvasRight" aria-labelledby="offcanvasRightLabel">
            <div class="offcanvas-body">
                <button type="button" class="btn-close text-reset float-end" data-bs-dismiss="offcanvas"
                    aria-label="Close"></button>
                <h3 class="mt-5" id="offcanvasRightLabel">{{ player.club }} Roster</h3>
                <p class="lead">Select player from list</p>
                <ul class="list-group ">
                    <li v-for="(teamMates, index) in team" @click="setPlayer(teamMates.id)" data-bs-dismiss="offcanvas"
                        :key="index" class="list-group-item list-group-item-action action">
                        {{ teamMates.first_name }} {{ teamMates.last_name }} <span class="text-muted">({{ teamMates.position }})</span>
                    </li>
                </ul>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "TeamRoster",
    props: ["player", "allPlayers"],
    data() {
        return {
            team: []
        };
    },
    created() {
        this.getTeamMates();
    },
    methods: {
        getTeamMates() {
            let that = this;
            this.team = that.allPlayers.filter(player => {
                return that.player.club == player.club;
            });
            that.team.sort((a, b) =>
                a.last_name > b.last_name ? 1 : b.last_name > a.last_name ? -1 : 0
            );
        },
        setPlayer(id) {
            this.$emit("setPlayer", id);
        }
    }
};
</script>

<style scoped>
.list-group-item {
    cursor: pointer;
}
</style>