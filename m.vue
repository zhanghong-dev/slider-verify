<style scoped>

    @import url('./iconfont.css');



    .portal-component__slider-verify {
        position: absolute;
        left: 0;
        top: 0;
        display: flex;
        flex-direction: column;
        justify-content: flex-start;
        align-items: center;
        width: 100%;
        height: 100%;
        border-radius: 4vw;
        background-color: #FFFFFF;
    }

    .portal-component__slider-verify * {
        -webkit-user-select: none;
        -moz-user-select: none;
        -ms-user-select: none;
        user-select: none;
    }



    /**
     * svg
     */

    .portal-component__slider-verify__svg {
        display: block;
        width: 76vw;
        height: 42.75vw;
        margin-top: 6.666666666666667vw;
        background-color: #E5E5E5;
    }

    .portal-component__slider-verify__svg .loading circle {
        transform-origin: 50%;
        -webkit-animation: slider-verify__loading 2s linear infinite;
        -o-animation: slider-verify__loading 2s linear infinite;
        animation: slider-verify__loading 2s linear infinite;
    }

    @keyframes slider-verify__loading {

        0% {
            stroke-dasharray: 20, 4000;
            stroke-dashoffset: 0;
        }

        50% {
            stroke-dasharray: 1800, 3000;
            stroke-dashoffset: -800;
        }

        to {
            transform: rotate(1turn);
            stroke-dasharray: 20, 4000;
            stroke-dashoffset: -2400;
        }

    }



    /**
     * bar
     */

    .portal-component__slider-verify__bar {
        position: relative;
        width: 76vw;
        height: 9.333333333333333vw;
        margin-top: 2.666666666666667vw;
        background-color: #E5E5E5;
    }

    .portal-component__slider-verify__bar .at__progress {
        position: absolute;
        left: 0;
        top: 0;
        width: 9.333333333333333vw;
        height: 9.333333333333333vw;
        background-color: #FFFF99;
    }

    .portal-component__slider-verify__bar .at__handle {
        position: absolute;
        z-index: 2;
        right: 0;
        top: 0;
        display: flex;
        justify-content: center;
        align-items: center;
        width: 9.333333333333333vw;
        height: 9.333333333333333vw;
        box-shadow: 0 0 1.333333333333333vw rgba(0, 0, 0, .3);
        color: #1A1A1A;
        background-color: #FFFFFF;
    }

    .portal-component__slider-verify__bar .at__text {
        position: absolute;
        z-index: 1;
        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);
        font-size: 4vw;
        line-height: 9.333333333333333vw;
        white-space: nowrap;
        color: #1A1A1A;
    }



    /**
     * __wave-light
     */

    .portal-component__slider-verify.__wave-light .portal-component__slider-verify__bar .at__text {
        -webkit-text-fill-color: transparent;
        -webkit-background-clip: text;
        background-image: -webkit-linear-gradient(left, #1A1A1A 0%, #CCCCCC 25%, #1A1A1A 50%, #CCCCCC 75%, #1A1A1A 100%);
        background-position: 0 0;
        background-size: 200% 100%;
        -webkit-animation: slider-verify__wave-light 2s linear infinite;
        -o-animation: slider-verify__wave-light 2s linear infinite;
        animation: slider-verify__wave-light 2s linear infinite;
    }

    @keyframes slider-verify__wave-light {

        to {
            background-position: -100% 0;
        }

    }



    /**
     * __success, __error
     */

    .portal-component__slider-verify.__success .portal-component__slider-verify__bar,
    .portal-component__slider-verify.__success .portal-component__slider-verify__bar .at__progress {
        background-color: #67C23A;
    }

    .portal-component__slider-verify.__error .portal-component__slider-verify__bar,
    .portal-component__slider-verify.__error .portal-component__slider-verify__bar .at__progress {
        background-color: #F56C6C;
    }

    .portal-component__slider-verify.__success .portal-component__slider-verify__bar .at__text,
    .portal-component__slider-verify.__error .portal-component__slider-verify__bar .at__text {
        color: #FFFFFF;
    }

</style>

<template>
    <div class="portal-component__slider-verify"
        :class="{
            '__wave-light'      : status.value === '',
            '__success'         : status.value === 'success',
            '__error'           : status.value === 'error'
        }">

        <!-- 插槽 -->
        <slot></slot>



        <!-- 滑块拼图 -->
        <svg class="portal-component__slider-verify__svg" :viewBox="svgViewBox">
            <defs>

                <image
                    id="image"
                    :xlink:href="image"
                    :width="svg.width"
                    :height="svg.height">
                </image>

                <path
                    id="slider"
                    d="
                        M896.72849294 487.95381419l-72.13622841 0
                        L824.59226453 295.59014969c0-53.14075534-43.04166002-96.18241422-96.18241422-96.18241422
                        L536.04502187 199.40773547l0-72.13622841c0-66.36598272-53.86145337-120.22743609-120.22743609-120.22743609
                        S295.59014969 60.90552434 295.59014969 127.27150706l0 72.13622841
                        L103.22648519 199.40773547c-53.14075534 0-95.70156089 43.04166002-95.70156089 96.18241422l-0.24100864 182.7454225 71.89638372 0c71.65537507 0 129.84567694 58.19030187 129.84567694 129.84567695s-58.19030187 129.84567694-129.84567694 129.84567694
                        L7.28508075 738.02692722l-0.24100864 182.74542251c0 53.14075534 43.04166002 96.18241422 96.18241422 96.18241422l182.7454225 0 0-72.13622841c0-71.65537507 58.19030187-129.84567694 129.84567695-129.84567695s129.84567694 58.19030187 129.84567694 129.84567695l0 72.13622841 182.74542251 0c53.14075534 0 96.18241422-43.04166002 96.18241422-96.18241422
                        L824.59109945 728.40985031l72.13622841 0c66.36598272 0 120.22743609-53.86145337 120.22743609-120.22743609
                        S963.09331058 487.95381419 896.72849294 487.95381419z
                    ">
                </path>

                <clipPath
                    id="clipPath">
                    <use
                        xlink:href="#slider"
                        :x="svg.slider.elBlack.x"
                        :y="svg.slider.elBlack.y">
                    </use>
                </clipPath>
            </defs>



            <!-- 滑块（黑色）、底图 -->
            <g>

                <use
                    xlink:href="#image"
                    x="0"
                    y="0">
                </use>

                <use
                    xlink:href="#slider"
                    :x="svg.slider.elBlack.x"
                    :y="svg.slider.elBlack.y"
                    stroke-width="30"
                    stroke="#FFFFFF"
                    fill="#1A1A1A">
                </use>
            </g>



            <!-- 滑块（彩色） -->
            <g>

                <use
                    xlink:href="#image"
                    clip-path="url(#clipPath)"
                    :x="svg.slider.elColour.x - svg.slider.elBlack.x"
                    :y="0">
                </use>

                <use
                    xlink:href="#slider"
                    :x="svg.slider.elColour.x"
                    :y="svg.slider.elBlack.y"
                    stroke-width="30"
                    stroke="#FFFFFF"
                    fill="none">
                </use>
            </g>



            <!-- loading -->
            <g v-if=" status.loading " class="loading">
                <circle
                    cx="50%"
                    cy="50%"
                    r="400"
                    stroke="#FFFFFF"
                    stroke-width="40"
                    stroke-dasharray="1800, 3000"
                    stroke-dashoffset="0"
                    stroke-linecap="round"
                    fill="none">
                </circle>
            </g>
        </svg>



        <!-- 拖拽条 -->
        <div class="portal-component__slider-verify__bar">

            <div class="at__progress"
                :style="{
                    'width': barProgressWidth
                }">
                <i ref="barHandle" class="at__handle"
                    :class="{
                        'go'            : status.value === '',
                        'success'       : status.value === 'success',
                        'error'         : status.value === 'error'
                    }">
                </i>
            </div>

            <div v-if=" text " class="at__text">
                {{ text }}
            </div>
        </div>
    </div>
</template>

<script>

    export default {

        props: {

            value: {
                type: Array
            },

            toleranceValue: {
                type: Number
            },

            image: {
                type: String
            },

            text: {
                type: String
            }

        },

        computed: {

            svgViewBox() {

                return '0 0 ' + this.svg.width + ' ' + this.svg.height;

            },

            svgSliderRM() {

                return this.svg.width / 30;

            },

            svgSliderRW() {

                return this.svg.width - this.svg.slider.size - this.svgSliderRM * 2;

            },

            svgSliderRH() {

                return this.svg.height - this.svg.slider.size - this.svgSliderRM * 2;

            },

            barProgressWidth() {

                return (this.sliding.width + 9.333333333333333) + 'vw';

            }

        },

        methods: {



            /**
             * MVC 的 C 层方法
             */

            init() {

                this.svg.slider.elBlack.x       = this.svgSliderRM + this.svgSliderRW / 2 + this.svgSliderRW / 2 * this.value[0];
                this.svg.slider.elBlack.y       = this.svgSliderRM + this.svgSliderRH * this.value[1];
                this.svg.slider.elColour.x      = this.svgSliderRM;
                this.sliding.width              = 0;
                this.sliding.startEvent         = null;
                this.status.value               = '';

            },

            asyncInit() {

                let done = () => {

                    this.status.loading = false;
                    setTimeout( () => this.init() );

                };

                this.status.loading = true;
                this.$emit('loading', done);

            },

            validator() {

                return this.svgSliderRW * this.toleranceValue > Math.abs(this.svg.slider.elBlack.x - this.svg.slider.elColour.x);

            },



            /**
             * MVC 的 C 层方法 slide*
             */

            slide($event) {

                let a = ($event.changedTouches[0].pageX - this.sliding.startEvent.changedTouches[0].pageX) / document.body.clientWidth * 100;

                if ( a < 0 )
                    a = 0;

                else if ( a > 66.66666666666667 )       // 76 - 9.333333333333333
                    a = 66.66666666666667;

                this.svg.slider.elColour.x = this.svgSliderRM + this.svgSliderRW * (a / 66.66666666666667);
                this.sliding.width = a;

            },

            slideStart($event) {

                if ( $event.target === this.$refs.barHandle && !this.status.value && !this.status.loading ) {

                    this.sliding.startEvent = $event;
                    document.addEventListener('touchmove', this.slide);
                    document.addEventListener('touchend', this.slideEnd);

                }

            },

            slideEnd($event) {

                document.removeEventListener('touchmove', this.slide);
                document.removeEventListener('touchend', this.slideEnd);

                if ( this.validator() )
                    this.status.value = 'success',
                    this.$emit('success');

                else
                    this.status.value = 'error',
                    this.asyncInit(),
                    this.$emit('error');

            }

        },

        created() {

            this.asyncInit();

        },

        mounted() {

            document.addEventListener('touchstart', this.slideStart);

        },

        data() {

            return {
                svg: {
                    width: 5760,
                    height: 3240,
                    slider: {
                        size: 1024,
                        elBlack: {
                            x: -1024,
                            y: -1024
                        },
                        elColour: {
                            x: -1024
                        }
                    }
                },
                sliding: {
                    width: 0,
                    startEvent: null
                },
                status: {
                    value: '',
                    loading: false
                }
            };

        }

    }

</script>
