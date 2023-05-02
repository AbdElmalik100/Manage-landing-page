<template>
    <header>
        <div :class="`overlay ${open ? 'active' : ''}`"></div>
        <div class="container d-flex align-items-center justify-content-between py-5">
            <img src="/images/logo.svg" alt="">
            <ul :class="`d-flex align-items-center gap-4 ${open ? 'active' : ''}`">
                <li>Pricing</li>
                <li>Product</li>
                <li>About Us</li>
                <li>Careers</li>
                <li>Community</li>
            </ul>
            <button class="butn">Get Started</button>
            <img @click="open = true" :class="`menu ${open ? 'active' : ''}`" src="/images/icon-hamburger.svg"
                alt="">
            <img @click="open = false" :class="`close ${open ? 'active' : ''}`" src="/images/icon-close.svg"
                alt="">
        </div>
    </header>
</template>
<script setup>
import { ref, watch } from 'vue';

const open = ref(false)

watch(open, newVal => {
    if (newVal === true) {
        document.body.style.overflow = 'hidden'
    } else document.body.style.overflow = 'visible'
})


</script>
<style lang="scss" scoped>
.overlay {
    display: none;
    position: absolute;
    width: 100%;
    height: 100%;
    left: 0;
    top: 0;
    background: linear-gradient(to bottom, rgba(116, 116, 116, 0.253), rgba(0, 0, 0, 0.699));
}

.close,
.menu {
    display: none;
}

header {

    ul {
        li {
            cursor: pointer;
            transition: 0.2s;
            color: var(--Very-Dark-Blue);

            &:hover {
                color: var(--Dark-Grayish-Blue);
            }
        }
    }

    @media (max-width:991px) {

        .close,
        .menu {
            cursor: pointer;
            position: relative;
            z-index: 55555;
        }

        .menu {
            display: block;

            &.active {
                display: none;
            }
        }

        .overlay.active {
            display: block;
        }

        .close.active {
            display: block;
        }

        ul {
            position: absolute;
            background-color: white;
            flex-direction: column;
            width: calc(100% - 24px);
            padding: 50px;
            left: 50%;
            transform: translateX(-50%);
            top: -100%;
            border-radius: 5px;
            transition: 0.2s;
            li {
                font-weight: bold;
            }

            &.active {
                top: 20%;

            }
        }

        button {
            display: none;
        }
    }
}</style>