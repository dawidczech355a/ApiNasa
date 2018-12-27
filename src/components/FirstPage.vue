<template>
    <div class="firstPageWrapper">
        <h1>
            NASA
        </h1>
        <b><p class="firstPageParagraph">
            Do you wanna learn more about universe?
        </p></b>
        <b><p class="firstPageParagraph">
            Checkout my page, search for a piece of space and enjoy learning. 
        </p></b>
    </div>
</template>

<script>
    export default {
        name: 'FirstPage',
    };
</script>

<style lang="scss" scoped>
    .firstPageWrapper {
        display: flex;
        text-align: center;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        margin-bottom: 20px;
        color: #00081c;
    }
    h1 {
        margin: 0;
        font-size: 35px;
        color: darkred;

        @media (min-width: 768px) {
            font-size: 68px;
        }
    }
    .firstPageParagraph {
        margin-top: 20px;
        font-size: 14px;

        @media (min-width: 768px) {
            font-size: 22px;
        }
    }
</style>
