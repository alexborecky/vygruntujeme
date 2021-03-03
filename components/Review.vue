<template>
    <div class="review flex">
        <div class="image" :style="{backgroundImage: 'url('+ image +')'}">
        </div>
        <div class="content">
            <h3>{{name}}</h3>
            <p class="title"><strong>{{title}}</strong></p>
            <p>{{review}}</p>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Review',
        props: [
            'image',
            'name',
            'review',
            'title'
        ]
    }
</script>

<style lang="scss" scoped>

.review {
    width: 52%;
    padding: 32px;
    margin: 40px 0;
    background-color: lighten($main-orange, 44%);
    box-shadow: 0 16px 24px rgba($color: #702800, $alpha: .16);
    border-radius: 24px;
    .image {
        width: 40px;
        height: 40px;
        background-position: center;
        background-size: cover;
        border-radius: 100px;
    }
    .content {
        max-width: 80%;
        margin-left: 24px;
        h3 {
            color: $main-orange;
        }
        .title {
            margin: 8px 0;
        }
    }
}

</style>