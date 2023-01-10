<template>
    <div class="card ">
        <div class="card-header bg-secondary">
            <div class="fs-5 text-light">Next {{ player.upcoming.length }} Games</div>
        </div>
        <table class="table table-striped mb-0 small">
            <thead>
                <tr>
                    <th>Date</th>
                    <th>Opponent</th>
                    <th>Time</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(game, index) in player.upcoming" :key="index">
                    <td>{{ formatMonth(game.date) }}</td>
                    <td>
                        <template v-if="player.club == game.away">
                            @ {{ removeCityFromTeamName(game.home) }}
                        </template>
                        <template v-else>
                            vs {{ removeCityFromTeamName(game.away) }}
                        </template>
                    </td>
                    <td>{{ formatTime(game.time) }} PM</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>


<script>
export default {
    name: "PlayerSchedule",
    props: ["player"],
    data() {
        return {};
    },
    methods: {
        removeCityFromTeamName(team) {
            let name = team.split(" ");
            return name[name.length - 1];
        },
        formatTime(time) {
            let timeSansSeconds = time.substring(0, 5);
            return this.removeZeroFirstChar(timeSansSeconds)
        },
        formatMonth(month) {
            let monthSansYear = month.substring(5);
            return this.removeZeroFirstChar(monthSansYear)
        },
        removeZeroFirstChar(string) {
            let firstChar = string.substring(0, 1);
            if (firstChar == "0") {
                string = string.substring(1);
            }
            return string
        },
    }
};
</script>
