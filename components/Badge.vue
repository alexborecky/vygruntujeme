<template>
    <div class="badge flex center">
        <img :src="image" alt="">
        <p class="bigger"><strong>{{service}}</strong></p>
    </div>
</template>

<script>
    export default {
        name: 'Badge',
        props: [
            'image',
            'service'
        ]
    }
</script>

<style lang="scss" scoped>

.badge {
    padding: 16px 56px;
    background-color: rgba($color: $main-orange, $alpha: .08);
    border-radius: 40px;
    margin: 16px;
    p { 
        color: $main-orange;
        font-weight: 600;
        margin-left: 16px;
    }
}

</style>