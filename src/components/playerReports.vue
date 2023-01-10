<template>
    <section class="card">
        <div class="card-header">
            <h4>Reports</h4>
        </div>
        <table class="table mb-0">
            <thead>
                <tr>
                    <th>Date</th>
                    <th>Scout</th>
                    <th width="75%">Details</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(report, reportIndex) in player.reports" :key="reportIndex">
                    <td>{{ report.date }}</td>
                    <td>{{ report.scout }}</td>
                    <td>
                        <a :href="`#reportDetails-${reportIndex}`" @click="scrollToBottom" data-bs-toggle="collapse"
                            class="btn btn-secondary text-light btn-sm text-secondary">View</a>
                        <table class="table mb-0 collapse" :id="`reportDetails-${reportIndex}`">
                            <tr>
                                <td colspan="2">
                                </td>
                                <td>
                                    <p class="mb-0">{{ report.summary }}</p>
                                    <PlayerReportTools :report="report" :reportType="_playerType"></PlayerReportTools>
                                </td>
                            </tr>
                        </table>

                    </td>

                </tr>

            </tbody>
        </table>
    </section>
</template>


<script>
import PlayerReportTools from "./playerReportTools.vue";
export default {
    name: "PlayerReports",
    props: ["player"],
    components: { PlayerReportTools },
    data() {
        return {};
    },
    methods: {
        scrollToBottom() {
            let pageBottom = document.querySelector("#page-bottom");
            pageBottom.scrollIntoView();
        }
    },
    computed: {
        _playerType() {
            return this.player.hitting_stats.length == 0 ? "pitcher" : "other";
        }
    }
};
</script>

<style scoped>
@media (min-width: 1024px) {}
</style>
