<template>
    <div class="container">
        <div class="row">
            asd
        </div>
        <div class="footer__copyright">
            © {{ dateYear }} Viblo. All rights reserved.
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            const date = new Date()
            const dateYear = date.getFullYear()

            return {
                dateYear
            }
        }
    }
</script>


<style lang="scss">
    .app-footer {
        text-align: center;
    }
</style>
