<template>
    <div>
        <div class="container">
            <div class="box">
                <img ref="drawTable" class="center-fit" src="../assets/FloorPlan.jpg" />
            </div>
            <div class="box stack-top">
                <div class="tile" v-for="item in division" :id="item.id"  :class="item.blinkClass" :ref="item.id" :style="{'background-position-x' : item.background_position_x,'background-position-y' : item.background_position_y, 'background-image':item.backgroundImage,  'background': item.background, 'margin-bottom': item.marginBottom,'margin-right': item.marginRight, 'background-color': item.backgroundcolor, 'width':item.width, 'height':item.height }" :key="item.id">
                </div>
            </div>
        </div>
    </div>
</template>
<script>
    export default {
        mounted() {
            var bwidth = 972;
            var bheight = 600;
            this.n_Tiles = this.defaults.x * this.defaults.y;
            for (var i = 0; i < this.n_Tiles; i++) {

                var cssPorps = {
                    id: i,
                    width: (bwidth / this.defaults.x) - this.defaults.gap + "px",
                    height: (bheight / this.defaults.y) - this.defaults.gap + "px",
                    marginBottom: "1px",
                    marginRight: "1px",
                    //backgroundcolor: "#d3f6db",
                    //backgroundImage: "url(http://1.bp.blogspot.com/-8PfnHfgrH4I/TylX2v8pTMI/AAAAAAAAJJ4/TICBoSEI57o/s1600/search_by_image_image.png)"
                };


                if (i == 412 || i == 413 || i == 452 || i == 453) {
                    cssPorps.blinkClass = "blink_me_red";
                }

                if (i == 512 || i == 513 || i == 552 || i == 553) {
                    cssPorps.blinkClass = "blink_me_orange";
                }
                //else {
                //    cssPorps.blinkClass = "blink_me_green";
                //}

              
                this.division.push(cssPorps);

            }
        },
        name: 'HelloWorld',
        data: function () {
            return {
                defaults: {
                    x: 40, // tiles in x axis
                    y: 30, // tiles in y axis
                    gap: 1
                },
                n_Tiles: 0,
                division: []

            }
        },
        methods: {
            ShowGrid: function () {
                
            },

            positionImage: function () {

                
            }


        }
    }
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

    .tile {
        float: left;
        -webkit-transition: all .1s linear;
        -moz-transition: all .1s linear;
        -ms-transition: all .1s linear;
        -o-transition: all .1s linear;
        /*background-image:url("../assets/FloorPlan.jpg");*/
    }

        .tile:hover {
            /*opacity: .65;*/
            background-color: red;
        }
    .blink_me_red {
        animation: blinker 1s linear infinite;
        background-color: red;
    }

    .blink_me_orange {
        animation: blinker 1s linear infinite;
        background-color: orange;
    }

    @keyframes blinker {
        50% {
            opacity: 0;
        }
    }

    .imgbox {
        display: grid;
        height: 100%;
    }

    .center-fit {
        max-width: 100%;
        max-height: 100%;
    }

    .container {
        height: 600px;
        max-width: 972px;
        position: relative;
        margin: auto;
    }

    .box {
        width: 100%;
        height: 100%;
        position: absolute;
        top: 0;
        left: 0;
        opacity: 0.8; /* for demo purpose  */
    }

    .stack-top {
        z-index: 9;
        width: 100%;
        height: 100%;
        /*margin: 40px;*/ /* for demo purpose  */
    }
</style>
