<template lang="pug">
    h1 Single User with ID: {{ $route.params.id }}
</template>
<script>
export default {
    validate (data) {
        // レンダリングする前の情報がdataに入る
        console.log(data)
        return /^\d+$/.test(data.params.id)
    }
}
</script>