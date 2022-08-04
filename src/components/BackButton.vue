<script>
export default {
    name: 'BackButton',
    props: {
        address: {
            type: String,
            default: 'https://ec2.zhuxiaotan.xyz'
        },
        pageName: {
            type: String,
            default: 'Welocome Page'
        }
    }
}
</script>

<template>
    <a :href="address">Back to {{ pageName }}</a>
</template>

<style scoped>
a {
    position: fixed;
    top: 15px;
    left: 15px;
}

i {
    font-style: normal;
}
</style>