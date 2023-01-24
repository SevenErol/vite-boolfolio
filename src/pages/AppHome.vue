<script>

import AppHeader from '../components/AppHeader.vue';

import AppBanner from '../components/AppBanner.vue';

export default {
    name: 'AppHome',
    components: { AppHeader, AppBanner }
}
</script>

<template>

    <AppHeader />

    <AppBanner />

    <section class="position-relative g-0 m-0 p-0">

        <div class="container">

            <div class="row align-items-center p-0 m-0 g-0">

                <div class="col-10 p-5 animate__animated animate__fadeInDown">

                    <h1>My story</h1>
                    <p class="lead">
                        Hi! I am Lorenzo, a new entry in the world of web development. After spending some years working
                        as
                        a workman in various factories i finally discovered and studied my true passion: CODING!
                    </p>
                    <p>I am a 25 years old boy based in Italy, more specifically in Milan. Since i was in high school i
                        had
                        the exact same question that probably affects everybody at that age, which is "What am i gonna
                        do
                        next?". Well i wasn't so lucky to understand it quickly so i decided to roll up my sleeve and
                        work
                        as a workman, but i never stopped thinking about my path. After five years of work, with even
                        some
                        gratifications, i finally landed on the idea that coding could have been the right career. I
                        decided
                        to invest on myself and put all my efforts in a coding bootcap called "Boolean" which is the
                        number
                        one choice in Italy for an intensive course of web development. 6 months after this amazing
                        experience i can proudly say i can code with various important programming languages such as:
                        HTML,
                        CSS, Javascript, Bootstrap, Vue js, PHP and Laravel. In conclusion i am a full-stack web
                        developer
                        with an increasing hungry to learn and curiosity for every aspect of this amazing job. </p>

                </div>

                <div class="col-2 animate__animated animate__fadeInDown">
                    <img src="../../public/img/Foto-Lori.jpg" alt="" class="img-fluid g-0">
                </div>

                <img src="../../public/img/wave.png" alt=""
                    class="img-fluid position-absolute bottom-0 start-50 translate-middle-x">

            </div>

        </div>



    </section>


</template>


<style lang="scss" scoped>
section {
    background-color: #f1f1f1;
    width: 100%;

    .container {
        height: calc(100vh - 230px);

        .position-absolute {
            height: 200px;
            padding: 0;
            margin: 0;
        }

    }
}
</style>