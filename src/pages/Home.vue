<script setup>
    import { onMounted, nextTick, onUnmounted } from 'vue';

    import PreLoader from '../components/Pre-Loader.vue';
    import Hero from '../components/Hero.vue'
    import WelcomeIntro from '../components/Welcome-Intro.vue';
    import About from '../components/About.vue';
    import Skill from '../components/Skill.vue';
    import Portfolio from  '../components/Portfolio.vue'
    import Service from '../components/Service.vue'
    import Features from '../components/Features.vue';
    import Testimonial from '../components/Testimonial.vue'
    import Blog from '../components/Blog.vue'
    import Partner from '../components/Partner.vue'
    import Contact from '../components/Contact.vue'

    let grid = null
    let swiper1 = null
    let swiper2 = null
    let map = null

    onMounted(async () => {
        await nextTick();

        /* ===============================
            Preloader
        =============================== */
        if ($('.js-preloader').length) {
            $('.js-preloader').fadeOut(400)
        }

        /* ===============================
            Text animation
        =============================== */
        if ($('#tech-tools').length) {
            $('#tech-tools').textition({
            animation: 'ease-out',
            map: { x: 200, y: 100, z: 0 },
            autoplay: true,
            interval: 3,
            speed: 1
            })
        }

        /* ===============================
            Isotope
        =============================== */
        if ($('.grid').length) {
            grid = $('.grid').isotope()

            grid.imagesLoaded().progress(() => {
            grid.isotope('layout')
            })

            $('.filter-button-group').on('click', 'button', function () {
            const filterValue = $(this).attr('data-filter')
            grid.isotope({ filter: filterValue })
            })
        }

        /* ===============================
            Swiper – testimonial
        =============================== */
        if (document.querySelector('.swiper')) {
            swiper1 = new Swiper('.swiper', {
            loop: true,
            spaceBetween: 24,
            autoplay: { delay: 5000 },
            breakpoints: {
                1200: { slidesPerView: 3 },
                992: { slidesPerView: 2 },
                576: { slidesPerView: 1 }
            },
            pagination: {
                el: '.swiper-pagination',
                clickable: true
            }
            })
        }

        /* ===============================
            Swiper – partner
        =============================== */
        if (document.querySelector('.partnerCarousel')) {
            swiper2 = new Swiper('.partnerCarousel', {
            loop: true,
            spaceBetween: 24,
            autoplay: { delay: 5000 },
            breakpoints: {
                1200: { slidesPerView: 6 },
                992: { slidesPerView: 4 },
                576: { slidesPerView: 3 },
                320: { slidesPerView: 2 }
            }
            })
        }

        /* ===============================
            Map (Leaflet)
        =============================== */
        if (document.getElementById('mapwrapper')) {
            map = L.map('mapwrapper').setView([-37.81716, 144.955937], 12)

            L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png').addTo(map)

            L.marker([-37.81716, 144.955937]).addTo(map)
        }

        /* ===============================
            Navbar fixed
        =============================== */
        const scrollHandler = () => {
            const offset = $('.hero-area').height()
            if ($(window).scrollTop() >= offset) {
            $('.site-header nav').addClass('fixed-top')
            } else {
            $('.site-header nav').removeClass('fixed-top')
            }
        }

        window.addEventListener('scroll', scrollHandler)

        /* ===============================
            Counter
        =============================== */
        if ($('.counter').length) {
            $('.counter').counterUp({
            delay: 10,
            time: 3000
            })
        }

        /* ===============================
            Progress bar
        =============================== */
        if (document.getElementById('skill-section')) {
            new Waypoint({
            element: document.getElementById('skill-section'),
            handler: function () {
                $('.progress .progress-bar').css('width', function () {
                return $(this).attr('aria-valuenow') + '%'
                })
            },
            offset: 700
            })
        }

        /* ===============================
            AOS
        =============================== */
        AOS.init({ once: true })
    })

    onUnmounted(() => {
        swiper1?.destroy()
        swiper2?.destroy()
        map?.remove()
    })

</script>

<template lang="html">
	<PreLoader />
    <Hero />
    <WelcomeIntro />
    <About />
    <Skill />
    <Portfolio />
    <Service />
    <Features />
    <Testimonial />
    <Blog />
    <Partner />
    <Contact />
</template>
