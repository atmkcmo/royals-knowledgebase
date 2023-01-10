<template>
    <div class="">
        <!-- pitchers -->
        <table v-if="reportType == 'pitcher'" class="table table-bordered text-center">
            <thead>
                <tr class="bg-light">
                    <td class="" colspan="2">Change Up</td>
                    <td colspan="2">Command</td>
                    <td colspan="2">Curve Ball</td>
                    <td colspan="2">Fast Ball</td>
                    <td colspan="2">Slider</td>
                </tr>
            </thead>
            <tbody>
                <tr class="small">
                    <td>Future:
                        <span class="fw-bold">
                            {{ report.tools.changeup_future }}
                        </span>
                    </td>
                    <td>Present:
                        <span class="fw-bold">{{ report.tools.changeup_present }}</span>
                    </td>
                    <td>Future:
                        <span class="fw-bold">{{ report.tools.command_future }}</span>

                    </td>
                    <td>Present:
                        <span class="fw-bold">{{ report.tools.command_present }}</span>

                    </td>
                    <td>Future:
                        <span class="fw-bold">{{ report.tools.curveball_future }}</span>

                    </td>
                    <td>Present:
                        <span class="fw-bold">{{ report.tools.curveball_present }}</span>

                    </td>
                    <td>Future:
                        <span class="fw-bold">{{ report.tools.fastball_future }}</span>

                    </td>
                    <td>Present:
                        <span class="fw-bold">{{ report.tools.fastball_present }}</span>

                    </td>
                    <td>Future:
                        <span class="fw-bold">{{ report.tools.slider_future }}</span>

                    </td>
                    <td>Present:
                        <span class="fw-bold">{{ report.tools.slider_present }}</span>

                    </td>
                </tr>
            </tbody>
        </table>
        <!-- pitchers -->

        <!-- hitters -->
        <table v-else class="table table-bordered text-center small table-sm">
            <thead>
                <tr>
                    <td colspan="2">Arm</td>
                    <td colspan="2">Fielding</td>
                    <td colspan="2">Hitting</td>
                    <td colspan="2">Power</td>
                    <td colspan="2">Speed</td>
                </tr>
            </thead>
            <tbody>
                <tr class="small">
                    <td>
                        Future:
                        <span class="fw-bold">{{ report.tools.arm_future }}</span>
                    </td>
                    <td>
                        Present:
                        <span class="fw-bold">{{ report.tools.arm_present }}</span>
                    </td>
                    <td>
                        Future:
                        <span class="fw-bold">{{ report.tools.fielding_future }}</span>
                    </td>
                    <td>
                        Present:
                        <span class="fw-bold">{{ report.tools.fielding_present }}</span>

                    </td>
                    <td>
                        Future:
                        <span class="fw-bold">{{ report.tools.hitting_future }}</span>
                    </td>
                    <td>
                        Present:
                        <span class="fw-bold">{{ report.tools.hitting_present }}</span>
                    </td>
                    <td>
                        Future:
                        <span class="fw-bold">{{ report.tools.power_future }}</span>
                    </td>
                    <td>
                        Present:
                        <span class="fw-bold">{{ report.tools.power_present }}</span>
                    </td>
                    <td>
                        Future:
                        <span class="fw-bold">{{ report.tools.speed_future }}</span>
                    </td>
                    <td>
                        Present:
                        <span class="fw-bold">{{ report.tools.speed_present }}</span>
                    </td>
                </tr>
            </tbody>
        </table>
        <!-- hitters -->
    </div>
</template>


<script>
export default {
    name: "PlayerReportTools",
    components: {},
    props: ['report', 'reportType'],
    data() {
        return {};
    },
};
</script>
