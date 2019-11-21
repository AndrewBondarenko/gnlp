<template>
    <div>
        <div class="desktop">

            <div class="desktop_left_gorgona">
                <h1>gorGOna</h1>
            </div>

            <div class="desktop_left_bar">
                <ul>
                    <li v-for="item in array">
                        {{ items[item-1].name }}
                    </li>
                </ul>

            </div>

            <div class="container">
                <div class="block">

                    <div v-if="step === 0" class="block-zero">
                        <div class="block_title">
                            <h1>WELCOME</h1>
                        </div>
                        <div class="welcome">
                            <div class="welcome-text">
                                <div class="welcome-text-description">
                                    <h1>WE</h1>
                                    <div class="gorgona">
                                        <h1>gorGOna</h1>
                                    </div>
                                    <h1>FAMILY!</h1>
                                </div>
                                <h1>ENJOY</h1>
                            </div>
                            <div class="welcome-button">
                                <button @click="step = 1">START</button>
                            </div>
                        </div>
                    </div>

                    <div v-if="step === 1" class="block-one">
                        <div class="block_title">
                            <h1>Select several topics that interest you.</h1>
                        </div>
                        <div class="block-one-content">
                            <div class="content-set-item" @click="selectedItemsList">
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
                        <h1>WAIT A SECOND PLEASE</h1>
                    </div>

                </div>

                <div class="buttons">
                    <!--<div v-if="step > 0 " class="button-back">-->
                        <!--<button @click="goBackStep">BACK</button>-->
                    <!--</div>-->
                    <div v-if="step === 1" class="button-next">
                        <button @click="sumbitItems">SUBMIT</button>
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
                array: [],
                isSending: false,
                isSent: false,
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
        watch: {
            isSent: function(){
                setTimeout(()=>{
                    this.isSent = false
                },4000);
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
                this.array = [];

                var i;
                for (i = 0; i < x.length; i++) {
                    this.array.push(x[i].id)
                }
                console.log(this.array);
                return this.array
            },
            onSubmit(e) {
                e.preventDefault();
                let currentObj = this;
                this.isSending = true;

                this.axios.post('https://max-yuz.herokuapp.com/feedback', {
                    itemID: this.array,
                })
                    .then(function (response) {
                        currentObj.output = response.data;
                        currentObj.isSending = false;
                        currentObj.isSent = true;
                        console.log("ok");
                    })
                    .catch(function (error) {
                        currentObj.output = error;
                        currentObj.isSending = false;
                        console.log(error);
                    });
            },
        }
    }
</script>

<style scoped lang="sass">
    $blue: #dde8f0
    $gray: #edece8
    $dark_blue: #7CBBE9
    $black: #303641


    $set_yellow: #ffe884
    $set_blue: #b2ceff
    $set_green: #8da751
    $set_lite_green: #55b8ae
    $set_pink: #eccee2
    $set_dark_blue: #00a3e1
    $set_black: #373933
    $set_gray: #c1dee7
    $set_white: #f8f8f5

    body
        color: $set_black

    .desktop
        margin-top: 0
        background-color: $set_gray

    .desktop_left_gorgona
        position: absolute
        left: 25px
        top: 10px
        height: 40px
        width: 200px
        padding: 5px 15px
        background-color: $set_lite_green
        color: $set_white
        border-radius: 20px
        h1
            margin: -2px 10px 0 10px

    .desktop_left_bar
        position: absolute
        display: flex
        flex-direction: column
        left: 70px
        top: 75px
        ul
            padding: 0
        li
            display: flex
            margin: 10px 0
            width: 200px
            background-color: $set_yellow
            border-radius: 20px
            padding: 10px 15px

    .container
        width: 60%
        height: 90vh
        display: flex
        flex-direction: column
        margin: 35px auto
        background-color: $set_white
        border-radius: 25px

    .block
        width: 100%
        height: 100%

    .block_title
        width: max-content
        display: flex
        margin: 25px auto 25px -50px
        padding: 0 20px
        background-color: $set_blue
        border-radius: 20px

    .buttons
        display: flex
        justify-content: space-around
        width: 90%
        margin: auto
        height: 100px
        button
            width: 200px
            height: 45px
            background: none
            border: 2px solid $set_black
            color: $set_black
            font-weight: 600
            cursor: pointer
            outline: none
            border-radius: 25px
            &:hover
                background: $set_black
                color: whitesmoke
        .button-back
            margin-right: auto
        .button-next
            margin-left: auto
            margin-right: auto

    .block-zero
        width: 100%
        height: auto
        .welcome
            display: flex
            flex-direction: column
            margin: 50px auto
            .welcome-text
                margin-bottom: 50px
                .welcome-text-description
                    display: flex
                    flex-direction: row
                    width: max-content
                    margin: 50px auto 0 auto
                    h1
                        padding: 10px
                    .gorgona
                        background-color: $set_lite_green
                        border-radius: 20px
                        height: 40px
                        margin-top: 32px
                        color: $set_white
                        h1
                            padding: 5px 20px
                            margin-top: -7px
            .welcome-button
                button
                    width: 200px
                    height: 45px
                    background: none
                    border: 2px solid $black
                    color: $black
                    font-weight: 600
                    cursor: pointer
                    outline: none
                    border-radius: 25px
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
