<script>
export default {
    name: "AppHeader",
}
</script>

<template>

    <header>
        <div class="container-fluid g-0">
            <nav class="navbar navbar-expand-sm border-bottom" id="ms_nav">
                <div class="container">
                    <a class="navbar-brand" href="/">Lorenzo</a>
                    <button class="navbar-toggler d-lg-none" type="button" data-bs-toggle="collapse"
                        data-bs-target="#mainNav" aria-controls="mainNav" aria-expanded="false"
                        aria-label="Toggle navigation">
                        <span class="navbar-toggler-icon"></span>
                    </button>
                    <div class="collapse navbar-collapse" id="mainNav">
                        <ul class="navbar-nav ms-auto mt-2 mt-lg-0">
                            <li class="nav-item">
                                <router-link class="nav-link" :to="{ name: 'home' }" aria-current="page">Home <span
                                        class="visually-hidden">(current)</span></router-link>
                            </li>
                            <li class="nav-item">
                                <router-link class="nav-link" :to="{ name: 'projects' }">Portfolio</router-link>
                            </li>
                            <li class="nav-item">
                                <router-link class="nav-link" :to="{ name: 'about' }">About</router-link>
                            </li>
                            <li class="nav-item">
                                <router-link class="nav-link" :to="{ name: 'contacts' }">Contacts</router-link>
                            </li>
                        </ul>

                    </div>
                </div>
            </nav>
        </div>
    </header>

</template>

<style lang="scss" scoped>
.container-fluid {
    background-color: #0081C9;
    -webkit-box-shadow: 0 8px 6px -6px black;
    -moz-box-shadow: 0 8px 6px -6px black;
    box-shadow: 0 8px 6px -6px black;
    position: fixed;
    top: 0;
    left: 0;
    z-index: 1000;
    height: 57px;

    #mainNav {
        .nav-link {
            color: white;
        }
    }
}
</style>