<template>
    <div class="advantage flex center">
        <img :src="img" alt="">
        <div class="content">
            <h3>{{title}}</h3>
            <p>{{text}}</p>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Advantage',
        props: [
            'img',
            'title',
            'text'
        ]
    }
</script>

<style lang="scss" scoped>

.advantage {
    margin: 40px 0;
    img {
        max-height: 240px;
        order: 1;
        margin: 0 80px;
    }
    .content {
        order: 2;
        p {
            max-width: 480px;
            margin-top: 16px;
            color: rgba($color: #000000, $alpha: .56);
            font-weight: 400;
        }
    }
}

</style>