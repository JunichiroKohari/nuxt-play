<template lang="pug">
    div
        h1 Users page
        div
            input(
                type="text"
                v-model="userId"
            )
            button(
                @click="onLoadUser"
            ) Load User
            nuxt-child
</template>
<script>
export default {
    data() {
        return {
            userId: ''
        }
    },
    methods: {
        onLoadUser() {
            this.$router.push('/users/' + this.userId)
        }
    }
}
</script>