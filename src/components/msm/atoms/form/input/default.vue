<template>
    <input :type="type" :class="elClass" :id="type+'-'+gCount" :placeholder="elPlaceholder" :value="elValue">
</template>

<script>

    import globalFuncs from '../../../../../mixins/global'
    import compData from '../../../../../mixins/compData'
    import { bus } from '../../../../../main.js'
    import { globalCount } from '../../../../../main.js'

    export default {

        props: {
            tag: {
                type: String,
                default: 'input'
            },
            type: {
                type: String,
                default: 'text'
            },
            elPlaceholder: {
                default: 'Enter here'
            },
            elValue: '',
            elClass: '',
            elWrapClass: ''
        },
        data() {
            return {
                gCount: globalCount.counter
            }
        },
        methods: {},
        created() {
            bus.$emit('compInfo', {"tag":this.tag, "type":this.type});
            globalCount.counter = globalCount.counter + 1;
        },
        mixins: [ globalFuncs ]

    }

</script>

<style scoped>
    input[type=text],
    input[type=password],
    input[type=email],
    input[type=number],
    input[type=tel]{
        padding: 16px 10px 17px;
        font-weight: 600;
        font-size: 14px;
        line-height: 1;
        border-radius: 5px;
        box-shadow: inset 0 2px 0 0 #c6cacc;
        box-sizing: border-box;
        background-color: #ebf0f2;
        display: block;
        color: #2B3133;
        width: 100%;
        height: 50px;
        transition: all 0.2s ease-in-out;
        margin-bottom: 10px;
    }
    input[type=text]:last-of-type,
    input[type=password]:last-of-type,
    input[type=email]:last-of-type,
    input[type=number]:last-of-type,
    input[type=tel]:last-of-type,
    .form-num-wrap input {
        margin-bottom: 0;
    }
    input:focus {
        box-shadow: 0 0 3px 2px #00aeef, inset 0 2px 0 0 #c6cacc;;
    }
    :-ms-input-placeholder {
        font-weight: 400;
        color: #949899;
    }
    ::-webkit-input-placeholder {
        font-weight: 400;
        color: #949899;
    }
    input.currency {
        padding-left: 20px;
    }
    .error-input input {
        background-color: #fde8e9;
        color: #ed1c24;
        box-shadow: 0 0 4px 2px #ed1c24;
    }
    .error-input input:focus {
        box-shadow: 0 0 3px 2px #00aeef, inset 0 2px 0 0 #c6cacc;
    }
    .form-date-wrap.error-input {
        background-color: #fde8e9;
        color: #ed1c24;
        box-shadow: 0 0 4px 2px #ed1c24;
    }
    .error-input input:placeholder-shown {
        color: #ed1c24;
    }
    :-ms-input-placeholder {
        font: normal 14px 'Open Sans';
        color: #949899;
    }
    ::-webkit-input-placeholder {
        font: normal 14px 'Open Sans';
        color: #949899;
    }
</style>
