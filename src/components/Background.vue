<template>
    <div class="imageWrapper"></div>
</template>

<script>
export default {
    
}
</script>

<style lang="scss" scoped>
    .imageWrapper {
        &::after {
            content: '';
            background: rgba(0, 0, 0, .5);
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
        }

        top: 0;
        position: fixed;
        width: 100%;
        height: 100%;
        background-image: url(../assets/background.jpg);
        background-size: cover;
        z-index: -1;
    }
</style>


