<template>
    <div :id="id" class="content-item" :class="{ contentItemActive: isActive }" @click="isActive = !isActive">
        <div class="content-item-img">
            <img :src="picture" :alt="name">
        </div>
        <div class="content-item-info">
            <div class="content-item-name">
                <h4> {{ name }} </h4>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Items",
        props: {
            id: Number,
            name: String,
            picture: String
        },

        data(){
            return{
                isActive: false
            }
        },

    }
</script>

<style scoped lang="sass">
    $blue: #dde8f0
    $gray: #edece8
    $dark_blue: #7CBBE9
    $black: #303641

    .content-item
        display: flex
        flex-direction: column
        width: 130px
        height: 130px
        margin: 10px
        cursor: pointer
        .content-item-img
            width: 120px
            height: 120px
            box-sizing: border-box
            img
                display: flex
                margin: 0 10px
                height: 100px
                width: 100px
        .content-item-info
            width: 118px
            height: 16px
            box-sizing: border-box
            .content-item-name
                h4
                    width: 100px
                    margin: -10px 10px 0 10px

    .contentItemActive
        border: 2px solid $black
        box-sizing: border-box
        .content-item-img
            img
                margin: -2px 8px
        .content-item-info
            height: 16px
            .content-item-name
                height: 16px
                h4
                    margin: -10px 8px 0 8px



</style>
