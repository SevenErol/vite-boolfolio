<script>

export default {

    name: "LanguageCard",
    props: {
        language: String
    }

}

</script>


<template>

    <div class="col-3 gy-3">

        <div class="card align-items-center p-3">
            <img class="card-img-top img-fluid" :src="'/img/' + language + '.png'" :alt="language">
            <div class="card-body">
                <h4 class="card-title">Title</h4>
                <p class="card-text">Text</p>
            </div>
        </div>

    </div>

</template>


<style lang="scss" scoped>
.card {
    height: 100%;

    img {
        width: 120px;
    }
}
</style>