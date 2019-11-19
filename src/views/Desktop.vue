<template>
    <div>
        <div class="desktop">
            <div class="container">
                <div class="block">

                    <div v-if="step === 0" class="block-zero">
                        <div class="welcome">
                            <div class="welcome-text">
                                <h1>WELCOME</h1>
                            </div>
                            <div class="welcome-button">
                                <button @click="step = 1">START</button>
                            </div>
                        </div>
                    </div>

                    <div v-if="step === 1" class="block-one">
                        <div class="block_step">
                            <h1>Step: 1</h1>
                        </div>
                        <div class="block-one-content">
                            <div class="content-set-item">
                                <div class="content-item" v-model="item_1" :class="{ contentItemActive: isActive1 }" @click="isActive1 = !isActive1">
                                    <img src="../assets/images/icon_item.png" alt="">
                                </div>
                                <div class="content-item"  v-model="item_2" :class="{ contentItemActive: isActive2 }" @click="isActive2 = !isActive2">
                                    <img src="../assets/images/icon_item.png" alt="">
                                </div>
                                <div class="content-item" v-model="item_3" :class="{ contentItemActive: isActive3 }" @click="isActive3 = !isActive3">
                                    <img src="../assets/images/icon_item.png" alt="">
                                </div>
                                <div class="content-item" v-model="item_4" :class="{ contentItemActive: isActive4 }" @click="isActive4 = !isActive4">
                                    <img src="../assets/images/icon_item.png" alt="">
                                </div>
                                <div class="content-item" v-model="item_5" :class="{ contentItemActive: isActive5 }" @click="isActive5 = !isActive5">
                                    <img src="../assets/images/icon_item.png" alt="">
                                </div>
                                <div class="content-item" v-model="item_6" :class="{ contentItemActive: isActive6 }" @click="isActive6 = !isActive6">
                                    <img src="../assets/images/icon_item.png" alt="">
                                </div>
                                <div class="content-item" v-model="item_7" :class="{ contentItemActive: isActive7 }" @click="isActive7 = !isActive7">
                                    <img src="../assets/images/icon_item.png" alt="">
                                </div>
                                <div class="content-item" v-model="item_8" :class="{ contentItemActive: isActive8 }" @click="isActive8 = !isActive8">
                                    <img src="../assets/images/icon_item.png" alt="">
                                </div>
                                <div class="content-item" v-model="item_9" :class="{ contentItemActive: isActive9 }" @click="isActive9 = !isActive9">
                                    <img src="../assets/images/icon_item.png" alt="">
                                </div>

                            </div>
                        </div>
                    </div>
                    <div v-if="step === 2" class="block-one">
                        <div class="block_step">
                            <h1>Step: 2</h1>
                        </div>
                    </div>

                </div>

                <div class="buttons">
                    <div v-if="step > 0" class="button-back">
                        <button @click="goBackStep">BACK</button>
                    </div>
                    <div v-if="step > 0 && step <= 1" class="button-next">
                        <button @click="goNextStep">NEXT</button>
                    </div>
                </div>

            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Desktop",
        data(){
            return{
                step: 0,
                items: [],
                isActive1: false,
                isActive2: false,
                isActive3: false,
                isActive4: false,
                isActive5: false,
                isActive6: false,
                isActive7: false,
                isActive8: false,
                isActive9: false,
                item_1: 1,
                item_2: 2,
                item_3: 3,
                item_4: 4,
                item_5: 5,
                item_6: 6,
                item_7: 7,
                item_8: 8,
                item_9: 9,
            }
        },
        methods: {
            goNextStep: function () {
                this.step = this.step + 1;
                console.log(this.step)
            },
            goBackStep: function () {
                this.step = this.step - 1;
                console.log(this.step)
            },
        }
    }
</script>

<style scoped lang="sass">
    $blue: #dde8f0
    $gray: #edece8
    $dark_blue: #7CBBE9
    $black: #303641

    body
        color: #303641

    .container
        width: 60%
        height: 85vh
        display: flex
        flex-direction: column
        margin: 50px auto
        background-color: $blue

    .block
        width: 100%
        height: 100%

    .block_step
        width: max-content
        display: flex
        margin: 25px auto 25px 50px

    .buttons
        display: flex
        justify-content: space-around
        width: 90%
        margin: auto
        height: 100px
        button
            width: 150px
            height: 35px
            background: none
            border: 2px solid $black
            color: $black
            font-weight: 600
            cursor: pointer
            outline: none
            &:hover
                background: $black
                color: whitesmoke
        .button-back
            margin-right: auto
        .button-next
            margin-left: auto

    .block-zero
        width: 100%
        height: auto
        .welcome
            display: flex
            flex-direction: column
            margin: 100px auto
            .welcome-text
                margin-bottom: 50px
            .welcome-button
                button
                    width: 150px
                    height: 35px
                    background: none
                    border: 2px solid $black
                    color: $black
                    font-weight: 600
                    cursor: pointer
                    outline: none
                    &:hover
                        background: $black
                        color: whitesmoke

    .block-one
        margin: 0
        width: 100%
        height: 85%
        .block-one-content
            display: flex
            width: 100%
            margin: 0 auto
            .content-set-item
                display: flex
                width: 550px
                height: max-content
                margin: auto
                flex-direction: row
                flex-wrap: wrap
                justify-content: space-around
                .content-item
                    width: 120px
                    height: 120px
                    margin: 10px
                    img
                        display: flex
                        margin: 10px
                        height: 100px
                        width: 100px
                        padding: 4px
                        box-sizing: border-box

                .contentItemActive
                    img
                        border: 2px solid $black



</style>
