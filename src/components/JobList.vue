<template>
    <div class="list-wrapper">
        <p>Ordered by {{order}}</p>
        <transition-group name="list" tag="ul">
            <li v-for="job in orderedJob" :key="job.id">
                <h2>{{job.title}} In {{job.location}}</h2>
                <div class="salary-wrapper">
                    <RupeeIcon class="rupee-icon"/>
                    <p class="salary">{{job.salary}} rupees</p>
                </div>
                <div class="description">Lorem ipsum dolor sit amet consectetur, adipisicing elit. Iure aperiam, harum fugiat rerum voluptatum dolor voluptatem minima inventore dolorum! Saepe, architecto. Minima totam ullam excepturi aut accusamus quas illum error!</div>
            </li>
        </transition-group>
    </div>
</template>


<script lang="ts">
import { computed, defineComponent, PropType } from 'vue'
import { Job } from "../composition/jobs"
import { orderTerm } from '../composition/order';
import RupeeIcon from "../svg/RupeeSvg.vue"

export default defineComponent({
    name: "JobList",
    props: {
        jobList: {
        type: Array as PropType<Job[]>,
        required: true
    },
        order: {
        required: true,
        type: String as PropType<orderTerm>
    }
    },
    components: {
        RupeeIcon
    },
    setup(props) {
        const orderedJob = computed(() => {
            return [...props.jobList].sort((a: Job, b:Job) => {
                return a[props.order] > b[props.order] ? 1 : -1
            })
        })

        return{ orderedJob }
    }
})
</script>

<style scoped>
.salary-wrapper .rupee-icon {
    width: 30px;
    height: 30px;
    align-self: center;
}

.salary-wrapper .salary {
    color: #17bf66;
    font-weight: bold;
    margin: 10px 4px
}

.salary-wrapper {
    display: flex
}

.list-wrapper ul {
    margin: 20px 0;
    list-style: none;
    padding: 0;
}

.list-wrapper {
    max-width: 960px;
    margin: 40px auto;
}

.list-wrapper ul li {
    background: white;
    margin: 20px 0;
    padding: 20px 15px;
    border-radius: 5px;
}

.list-wrapper ul h2 {
    text-transform: capitalize;
    margin: 0 0 10px;
}

.list-wrapper ul .description {
    padding: 15px 0 20px 0;
}

.list-move {
    transition: all 1s;
}
</style>