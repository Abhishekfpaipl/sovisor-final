<template>
    <div class="py-5 text-white" style="background-color: var(--brand-color)">
        <h3 class="text-center mb-5 text-capitalize ">we rely on the best to provide the finest service and experience
        </h3>
        <article :class="['wrapper', { 'wrapper--vertical': isVertical }]">
            <div class="marquee" :class="{ 'marquee--vertical': isVertical }">
                <div class="marquee__group" :style="{ 'animation-direction': isReverse ? 'reverse' : 'normal' }">
                    <div v-for="(link, index) in links" :key="index" class="d-flex flex-column">
                        <img :src="link.image" style="width:80px;height:80px;object-fit: contain;filter: invert(1)"
                            alt="">
                        <p class="text-center mb-0">{{ link.name }}</p>
                    </div>
                </div>
                <div aria-hidden="true" class="marquee__group"
                    :style="{ 'animation-direction': isReverse ? 'reverse' : 'normal' }">
                    <div v-for="(link, index) in links" :key="index" class="d-flex flex-column">
                        <img :src="link.image" style="width:80px;height:80px;object-fit: contain; filter: invert(1)"
                            alt="">
                        <p class="text-center mb-0">{{ link.name }}</p>
                    </div>
                </div>
            </div>
        </article>
    </div>
</template>

<script> 

export default {
    name: "AutoScrolling",
    props: {
        brandColorOne: {
            type: String,
            default: '#000'
        }
    },
    data() {
        return {
            isVertical: false,
            isReverse: false,
            links: [
                {
                    id: 1,
                    name: 'Amazon',
                    image: '/img/amazon.png'
                },
                {
                    id: 2,
                    name: 'Apple',
                    image: "/img/apple.png"
                },
                {
                    id: 3,
                    name: 'Aws',
                    image: "/img/aws.png"
                },
                {
                    id: 4,
                    name: 'Facebook',
                    image: "/img/fb.png"
                },
                {
                    id: 5,
                    name: 'Google',
                    image: "/img/google.png"
                },
                {
                    id: 6,
                    name: 'Meta',
                    image: "/img/meta.png"
                },
                {
                    id: 7,
                    name: 'Microsoft',
                    image: "/img/microsoft.png"
                },
                {
                    id: 11,
                    name: 'Vodafone',
                    image: "/img/vodafone.png"
                },
            ]
        };
    },
    methods: {
        toggleDirection() {
            this.isVertical = !this.isVertical;
            this.isReverse = !this.isReverse;
        },
    },
};
</script>

<style>
:root {
    --color-text: navy;
    --color-bg: papayawhip;
    --color-bg-accent: #ecdcc0;
    --size: clamp(10rem, 1rem + 40vmin, 30rem);
    --gap: calc(var(--size) / 14);
    --duration: 10s;
    --scroll-start: 0;
    --scroll-end: calc(-100% - var(--gap));
}

.marquee {
    display: flex;
    overflow: hidden;
    user-select: none;
    gap: var(--gap);
    mask-image: linear-gradient(var(--mask-direction, to right),
            hsl(0 0% 0% / 0),
            hsl(0 0% 0% / 1) 20%,
            hsl(0 0% 0% / 1) 80%,
            hsl(0 0% 0% / 0));
}

.marquee__group {
    flex-shrink: 0;
    display: flex;
    align-items: center;
    justify-content: space-around;
    gap: var(--gap);
    min-width: 100%;
    animation: scroll-x var(--duration) linear infinite;
}

@media (prefers-reduced-motion: reduce) {
    .marquee__group {
        animation-play-state: paused;
    }
}

.marquee--vertical {
    --mask-direction: to bottom;
}

.marquee--vertical,
.marquee--vertical .marquee__group {
    flex-direction: column;
}

.marquee--vertical .marquee__group {
    animation-name: scroll-y;
}

.marquee--reverse .marquee__group {
    animation-direction: reverse;
    animation-delay: -3s;
}

@keyframes scroll-x {
    from {
        transform: translateX(var(--scroll-start));
    }

    to {
        transform: translateX(var(--scroll-end));
    }
}

@keyframes scroll-y {
    from {
        transform: translateY(var(--scroll-start));
    }

    to {
        transform: translateY(var(--scroll-end));
    }
}

/* Parent wrapper */
.wrapper {
    display: flex;
    flex-direction: column;
    gap: var(--gap);
    margin: auto;
    max-width: 100vw;
}

.wrapper--vertical {
    flex-direction: row;
    height: 100vh;
}

/* Toggle direction button */
.toggle {
    --size: 3rem;
    position: relative;
    position: fixed;
    top: 1rem;
    left: 1rem;
    width: var(--size);
    height: var(--size);
    font: inherit;
    text-align: center;
    cursor: pointer;
    outline: none;
    border: none;
    border-radius: 50%;
    color: inherit;
    background-color: var(--color-bg-accent);
    z-index: 1;
}

.toggle:focus-visible {
    box-shadow: 0 0 0 2px var(--color-text);
}

.toggle span {
    position: absolute;
    display: inline-block;
    top: 50%;
    left: calc(100% + 0.4em);
    width: fit-content;
    white-space: nowrap;
    transform: translateY(-50%);
    animation: fade 400ms 4s ease-out forwards;
    user-select: none;
}

@keyframes fade {
    to {
        opacity: 0;
        visibility: hidden;
    }
}
</style>