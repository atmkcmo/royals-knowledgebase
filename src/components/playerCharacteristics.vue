<template>
    <div class="d-flex">
        <ul class="list-group list-group-horizontal text-center">
            <li class="list-group-item">
                <span>Position</span><br>
                <span class="fw-bold">{{ player.position }}</span>
            </li>
            <li class="list-group-item">
                <span>Age</span><br>
                <span class="fw-bold">{{ getAge(player.birth_date) }}</span>
            </li>
            <li class="list-group-item">
                <span class="">Height</span><br>
                <span class="fw-bold">{{ player.height_feet }}' 
                    {{ player.height_inches ? player.height_inches : '0' }}"</span>
            </li>
            <li class="list-group-item">
                <span class="">Weight</span><br>
                <span class="fw-bold">{{ player.weight }} lbs</span>
            </li>
            <li class="list-group-item">
                <span class="">Throws</span><br>
                <span class="fw-bold">{{ getHand(player.throws) }}</span>
            </li>
            <li class="list-group-item">
                <span class="">Bats</span><br>
                <span class="fw-bold">{{ getHand(player.bats) }}</span>
            </li>
        </ul>
    </div>
</template>


<script>
export default {
    name: "PlayerCharacteristics",
    components: {},
    props: ["player"],
    data() {
        return {};
    },
    methods: {
        getHand(handAbbr) {
            return handAbbr == "R" ? "Right" : "Left";
        },
        getAge(dateString) {
            var today = new Date();
            var birthDate = new Date(dateString);
            var age = today.getFullYear() - birthDate.getFullYear();
            var m = today.getMonth() - birthDate.getMonth();
            if (m < 0 || (m === 0 && today.getDate() < birthDate.getDate())) {
                age--;
            }
            return age;
        }
    }
};
</script>
