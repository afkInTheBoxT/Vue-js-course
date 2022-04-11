<template>
    <div>
        <button v-on:click="GetRandom">Інформація про випадкову породи</button>
        <div>
            <h3 v-if="randomBreed[0] != null">Порода: {{randomBreed[0]}}</h3>
            <h4 v-if="randomBreed[1]?.length > 0">Підпороди:</h4>
            <h4>{{randomBreed[1]?.join(", ")}}</h4>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            randomBreed: Object
        }
    },
    props: ['breeds'],
    methods: {
        GetRandom() {
            this.randomBreed = this.breeds[Math.floor(Math.random() * this.breeds.length)];
        }
    }
}
</script>
