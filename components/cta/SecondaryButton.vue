<template>
    <a :href="link" target="_blank">
        <button>{{content}}</button>
    </a>
</template>

<script>
    export default {
        name: 'PrimaryButton',
        props: [
            'link',
            'content'
        ]
    }
</script>

<style lang="scss" scoped>

button {
    padding: 10px 32px;
    border-radius: 100px;
    border: none;
    background-color: $main-orange;
    color: white;
    font-weight: 600;
    font-size: 16px;
    letter-spacing: .4px;
    min-width: 200px;
    transition: .3s ease-in-out;
    box-shadow: 0 2px 0px darken($main-orange, 10%);
    &:focus {
        outline: none;
    }
}

a {
    margin: 24px;
    &:hover {
        button {
            background-color: darken($main-orange, 5%);
            transform: translateY(1px);
            box-shadow: none;
            cursor: pointer;
        }
    }
}

</style>