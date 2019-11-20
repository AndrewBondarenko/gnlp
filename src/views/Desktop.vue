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

                                <Items
                                        v-for="item in items"
                                        v-bind:id="item.id"
                                        v-bind:name="item.name"
                                        v-bind:picture="item.picture"
                                ></Items >

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
                    <div v-if="step === 1" class="button-next">
                        <button @click="sumbitItems">NEXT</button>
                    </div>
                    <div v-if="step > 0 && step <= 1 && step !== 1" class="button-next">
                        <button @click="goNextStep">NEXT</button>
                    </div>
                </div>

            </div>
        </div>
    </div>
</template>

<script>
    import Items from '../components/Items'

    export default {
        name: "Desktop",
        components:{
            Items
        },
        data(){
            return{
                step: 0,
                items: [
                    {id: 1, name:'GORGONA1', picture: require('@/assets/images/icon_item.png') },
                    {id: 2, name:'GORGONA2', picture: require('@/assets/images/icon_item.png') },
                    {id: 3, name:'GORGONA3', picture: require('@/assets/images/icon_item.png') },
                    {id: 4, name:'GORGONA4', picture: require('@/assets/images/icon_item.png') },
                    {id: 5, name:'GORGONA5', picture: require('@/assets/images/icon_item.png') },
                    {id: 6, name:'GORGONA6', picture: require('@/assets/images/icon_item.png') },
                    {id: 7, name:'GORGONA7', picture: require('@/assets/images/icon_item.png') },
                    {id: 8, name:'GORGONA8', picture: require('@/assets/images/icon_item.png') },
                    {id: 9, name:'GORGONA9', picture: require('@/assets/images/icon_item.png') },
                ]
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
            sumbitItems: function() {
                this.selectedItemsList();
                this.goNextStep();
            },
            selectedItemsList: function () {
                var x = document.getElementsByClassName("contentItemActive");
                var array = [];
                var i;
                for (i = 0; i < x.length; i++) {
                    array.push(x[i].id)
                }
                console.log(array);
                return array
            }
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





</style>
