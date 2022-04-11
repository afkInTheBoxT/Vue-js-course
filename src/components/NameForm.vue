<template>
            <form @submit.prevent="onSubmit">
                <input type="text" v-model="name">
                <button type="submit">Підтвердити</button>
            </form>
</template>



<script>

export default {
    data() {
        return {
            name: ''
        }
    },
    methods: {
        onSubmit() {
            console.log('Submit', this.name);

            if (this.name.trim()) {
                const newName = {
                    name: this.name,
                }
                this.$emit('change-name', newName);
            }
            else {
                const newName = {
                    name: "Незнайомець"
                }
                this.$emit('change-name', newName);
            }
        }
    }
}
</script>
