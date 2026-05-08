<script setup>
    import { RouterLink } from 'vue-router';
    const homeUrl = "/"
    const logo = '/assets/image/fungi_logo.png'
    const logoAlt = 'fungi logo'
</script>

<template lang="html">
    <!-- SITE HEADER -->
    <header class="site-header" id="site-header">
        <nav class="navbar navbar-expand-xl" id="site-navbar">
            <div class="container">
                <RouterLink class="navbar-brand" :to="homeUrl">
                    <img class="img-fluid" :src="logo" :alt="logoAlt">
                </RouterLink>
                <button class="navbar-toggler" type="button" data-bs-toggle="collapse"
                    data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent"
                    aria-expanded="false" aria-label="Toggle navigation">
                    <span class="navbar-toggler-icon"><i class="bi bi-list"></i></span>
                </button>
                <div class="collapse navbar-collapse" id="navbarSupportedContent">
                    <ul class="navbar-nav ms-auto mb-lg-0">
                        <li class="nav-item">
                            <RouterLink class="nav-link" aria-current="page" to="/test">Go to Test</RouterLink>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link active" aria-current="page" href="#site-header">Home</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link" href="#about-section">About</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link" href="#portfolio-section">Portfolio</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link" href="#service-section">Service</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link" href="#testimonial-section">Testimonials</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link" href="#blog-section">Blog</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link" href="#contact-section">Contact</a>
                        </li>
                    </ul> <!-- .navbar-nav -->
                </div> <!-- .collapse -->
            </div> <!-- .container -->
        </nav> <!-- .navbar -->
    </header> <!-- .site-header -->
</template>