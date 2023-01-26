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

        <div class="card align-items-center justify-content-between p-3 ms_border">

            <div class="align-self-center">

                <img class="card-img-top img-fluid" :src="'/img/' + language + '.png'" :alt="language">

            </div>

            <div class="ms_btn">
                <a href="#" class="btn btn-primary">Discover More</a>
            </div>

        </div>

    </div>




</template>


<style lang="scss" scoped>
.card {
    height: 312px;
    background-image: url(/img/tech-background.jpg);
    background-position: center;
    background-size: cover;
    background-repeat: no-repeat;

    img {
        width: 120px;
    }

    .ms_btn {
        width: 100%;

        .btn {
            width: 100%;
        }
    }

}
</style>