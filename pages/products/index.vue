<template lang="pug">
    div
        h1 Products Page
        input(
            type="text"
            v-model="productsId"
        )
        button(
            @click="onLoadProduct"
        ) Product Page
</template>
<script>
export default {
    data() {
        return {
            productsId: ''
        }
    },
    methods: {
        onLoadProduct () {
            this.$router.push('/products/' + this.productsId)
        }
    }
}
</script>