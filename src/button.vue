<template>
    <button class="m-button" :class="`icon-${iconPosition}`" @click="loading = !loading">
        <g-icon v-if="icon && !loading" :name="icon"></g-icon>
        <g-icon v-if="loading" name="loading" class="loading"></g-icon>
        <span class="content">
            <slot></slot>
        </span>
    </button>
</template>

<script>
    export default {
        // props: ['icon', 'iconPosition']
        props: {
            icon: {},
            iconPosition: {
                type: String,
                default: 'left',
                validator(value) {
                    return !(value !== 'left' && value !== 'right')
                }
            },
            loading: {
                type: Boolean,
                default: false
            }
        }
    }
</script>

<style lang="scss">
    @keyframes spin {
        0% { transform: rotate(0);}
        100% { transform: rotate(360deg);}
    }
    .loading {
        animation: spin 1s infinite linear;
    }
    .m-button {
        height: var(--button-height);
        padding: 0 1em;
        font: inherit;
        border-radius: var(--border-radius);
        border: 1px solid var(--border-color);
        background: var(--button-bg);
        display: inline-flex;
        justify-content: center;
        align-items: center;
        vertical-align: top;
        &:hover {
            border-color: var(--border-color-hover);
        }
        &:active {
            background: var(--button-active-bg);
        }
        &:focus {
            outline: none;
        }
    }

    .icon-left {
        > .icon {
            order: 1;
            margin-right: .3em;
        }
        > .content {
            order: 2;
        }
    }

    .icon-right {
        > .icon {
            margin-left: .3em;
            order: 2;
        }
        > .content {
            order: 1;
        }
    }



</style>