<template>
    <div class="sidebar">
        <div class="sidebar__logo">
            <img src="~/static/logo.png" alt="Logo">
        </div>

        <no-ssr>
            <ul>
                <li
                    v-for="(path,index) in sideBarPath"
                    :key="index"
                    :class="{'active': active(path)}"
                >
                    <a v-scroll-to="scroll(path)" href="#">{{ answerTitle(path) }}</a>
                </li>
            </ul>
        </no-ssr>
    </div>
</template>

<script>
    import _lowerCase from "lodash/lowerCase"
    import _keys from "lodash/keys"

    export default {
        props: {
            answers: {
                type: Array,
                required: true
            }
        },

        data() {
            let answerPath = this.answers.map(o => o.name)
            const customPath = ["overview"]
            const sideBarPath = [customPath, ...answerPath]

            return {
                sideBarPath
            }
        },

        methods: {
            scroll(name) {
                return {
                    el: `#${name}`,
                    duration: 500,
                    easing: "ease",
                    offset: 0,
                    force: true,
                    cancelable: true,
                    onStart: false,
                    onDone: function() {
                        document.location.hash = name
                    },
                    onCancel: false,
                    x: false,
                    y: true
                }
            },

            answerTitle(name) {
                return _lowerCase(name)
            },
            active(path) {
                return this.$route.hash === `#${path}`
            }
        }
    }
</script>

<style lang="scss">
    .sidebar {
        margin-top: 10px;

        &__logo {
            max-width: 180px;
            margin: 10px auto;

            img {
                width: 100%;
            }
        }

        ul {
            &::before {
                border-top: 1px solid #d2d3d4;
                content: "";
                display: block;
                padding: 3px 0;
                margin: 3px 0;
            }

            li {
                a {
                    color: black;
                    text-transform: capitalize;
                }
            }

            .active {
                a {
                    color: red;
                }
            }
        }
    }
</style>
