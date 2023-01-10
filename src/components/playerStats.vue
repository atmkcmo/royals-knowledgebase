<template>
    <div class="card">
        <div class="card-header">
            <h2 class="fs-4">Stats</h2>
        </div>
        <div class="table-responsive">
            <!-- hitters Stats -->
            <table class="table mb-0 table-bordered text-center" v-if="_playerType == 'hitter'">
                <thead class="table-light">
                    <tr>
                        <th scope="col" data-bs-toggle="tooltip" data-bs-placement="bottom" title="Year">
                            Year
                        </th>

                        <th scope="col" data-bs-toggle="tooltip" data-bs-placement="bottom" title="Average">
                            AVG
                        </th>

                        <!-- slugging -->
                        <th scope="col" data-bs-toggle="tooltip" data-bs-placement="bottom" title="Slugging">
                            SLG
                        </th>

                        <!-- At Bats -->
                        <th scope="col" data-bs-toggle="tooltip" data-bs-placement="bottom" title="At Bats">
                            AB
                        </th>

                        <!-- plate apperance -->
                        <th scope="col" data-bs-toggle="tooltip" data-bs-placement="bottom" title="Plate Apperances">
                            PA
                        </th>

                        <th scope="col" data-bs-toggle="tooltip" data-bs-placement="bottom" title="RBI">
                            RBI
                        </th>

                        <!-- bases on balls -->
                        <th scope="col" data-bs-toggle="tooltip" data-bs-placement="bottom" title="Bases on Balls">
                            BB
                        </th>

                        <th scope="col" data-bs-toggle="tooltip" data-bs-placement="bottom" title="Strikeouts">
                            K
                        </th>

                        <!-- on base percentage -->
                        <th scope="col" data-bs-toggle="tooltip" data-bs-placement="bottom" title="On Base Percentage">
                            OBP
                        </th>

                        <!-- hits by pitch -->
                        <th scope="col" data-bs-toggle="tooltip" data-bs-placement="bottom" title="Hit by Pitch">
                            HBP
                        </th>

                        <th scope="col" data-bs-toggle="tooltip" data-bs-placement="bottom" title="Runs">
                            R
                        </th>

                        <th scope="col" data-bs-toggle="tooltip" data-bs-placement="bottom" title="Doubles">
                            2B
                        </th>

                        <th scope="col" data-bs-toggle="tooltip" data-bs-placement="bottom" title="Triples">
                            3B
                        </th>

                        <th scope="col" data-bs-toggle="tooltip" data-bs-placement="bottom" title="Homeruns">
                            HR
                        </th>

                        <th scope="col" data-bs-toggle="tooltip" data-bs-placement="bottom" title="Stolen Bases">
                            SB
                        </th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(stats, index) in player.hitting_stats" :key="index">
                        <th>{{ stats.year }}</th>
                        <td>{{ stats.avg }}</td>
                        <td>{{ stats.slugging }}</td>
                        <td>{{ stats.at_bats }}</td>
                        <td>{{ stats.plate_appearances }}</td>
                        <td>{{ stats.rbi }}</td>
                        <td>{{ stats.bases_on_balls }}</td>
                        <td>{{ stats.strikeouts }}</td>

                        <td>{{ stats.on_base }}</td>

                        <td>{{ stats.hit_by_pitch }}</td>
                        <td>{{ stats.runs }}</td>
                        <td>{{ stats.doubles }}</td>
                        <td>{{ stats.triples }}</td>
                        <td>{{ stats.home_runs }}</td>
                        <td>{{ stats.stolen_bases }}</td>
                    </tr>
                </tbody>
            </table>

            <!-- pitches Stats -->
            <table v-else class="table table-bordered text-center mb-0">
                <thead class="table-light small">
                    <tr>
                        <th scope="col" data-bs-toggle="tooltip" data-bs-placement="bottom" title="Year">
                            Year
                        </th>
                        <th scope="col" data-bs-toggle="tooltip" data-bs-placement="top" title="ERA">
                            ERA
                        </th>
                        <th scope="col" data-bs-toggle="tooltip" data-bs-placement="bottom" title="Games">
                            G
                        </th>
                        <th scope="col" data-bs-toggle="tooltip" data-bs-placement="right" title="Games Started">
                            GS
                        </th>
                        <!-- innings pitched -->
                        <th scope="col" data-bs-toggle="tooltip" data-bs-placement="top" title="Innings Pitched">
                            IP
                        </th>

                        <th scope="col" data-bs-toggle="tooltip" data-bs-placement="top" title="Wins">
                            W
                        </th>
                        <th scope="col" data-bs-toggle="tooltip" data-bs-placement="top" title="Losses">
                            L
                        </th>
                        <th scope="col" data-bs-toggle="tooltip" data-bs-placement="top" title="Saves">
                            Saves
                        </th>

                        <!-- strikeouts -->
                        <th scope="col" data-bs-toggle="tooltip" data-bs-placement="top" title="Strikeouts">
                            SO
                        </th>
                        <!-- strikeout rate -->
                        <th scope="col" data-bs-toggle="tooltip" data-bs-placement="top" title="Strikeout Rate">
                            SOR
                        </th>

                        <th scope="col" data-bs-toggle="tooltip" data-bs-placement="top" title="Runs">
                            Runs
                        </th>
                        <!-- earned runs -->
                        <th scope="col" data-bs-toggle="tooltip" data-bs-placement="top" title="Earned Runs">
                            ER
                        </th>

                        <!-- balls on base-->
                        <th scope="col" data-bs-toggle="tooltip" data-bs-placement="top" title="Bases on Balls">
                            BB
                        </th>
                        <th scope="col" data-bs-toggle="tooltip" data-bs-placement="top" title="Bases on Balls Rate">
                            BBR
                        </th>
                        <th scope="col" data-bs-toggle="tooltip" data-bs-placement="top"
                            title="Intentional Base on Balls">
                            IBB
                        </th>
                        <th scope="col" data-bs-toggle="tooltip" data-bs-placement="top" title="Hits">
                            H
                        </th>
                        <th scope="col" data-bs-toggle="tooltip" data-bs-placement="top" title="Hits by Pitch">
                            HBP
                        </th>

                        <!-- Wild Pitches-->
                        <th scope="col" data-bs-toggle="tooltip" data-bs-placement="top" title="Wild Pitches">
                            WP
                        </th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(stats, index) in player.pitching_stats" :key="index">
                        <th>{{ stats.year }}</th>
                        <td>{{ stats.era.toFixed(2) }}</td>
                        <td>{{ stats.games }}</td>
                        <td>{{ stats.games_started }}</td>
                        <td>{{ stats.innings_pitched }}</td>

                        <td>{{ stats.wins }}</td>
                        <td>{{ stats.losses }}</td>
                        <td>{{ stats.saves }}</td>

                        
                        <td>{{ stats.strikeouts }}</td>
                        <td>{{ stats.k_rate.toFixed(3) }}</td>

                        <td>{{ stats.runs }}</td>
                        <td>{{ stats.earned_runs }}</td>

                        <td>{{ stats.bases_on_balls }}</td>
                        <td>{{ stats.bb_rate.toFixed(2) }}</td>
                        <td>{{ stats.intentional_bases_on_balls }}</td>
                        <td>{{ stats.hits }}</td>
                        <td>{{ stats.hit_by_pitch }}</td>

                        <td>{{ stats.wild_pitches }}</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>

<script>
export default {
    name: "StatsTable",
    props: ["player"],
    data() {
        return {};
    },
    computed: {
        _playerType() {
            return this.player.hitting_stats.length > 0 ? "hitter" : "pitcher";
        }
    }
};
</script>