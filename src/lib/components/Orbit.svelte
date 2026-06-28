<script lang="ts">
    import { socials } from "$lib/socials";
    import SocialLink from "./SocialLink.svelte";

    const radius = 170;
</script>

<div class="orbit">
    {#each socials as social, i}
        <div
            class="item"
            style={`--angle:${(360 / socials.length) * i}deg; --radius:${radius}px;`}
        >
            <div class="icon">
                <SocialLink {...social} />
            </div>
        </div>
    {/each}
</div>

<style>
    .orbit {
        position: absolute;

        width: 420px;
        height: 420px;

        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);

        display: grid;
        place-items: center;

        z-index: 1;

        animation: orbit 30s linear infinite;
    }

    .orbit:hover .icon {
        animation-play-state: paused;
    }

    .item {
        position: absolute;

        left: 50%;
        top: 50%;

        /* it would keep mispositioning itself and rot rotate in a perfect circle unless i did this :bart:  */
        width: 0;
        height: 0;

        transform: rotate(var(--angle)) translateX(var(--radius));
    }

    .icon {
        transform: translate(-50%, -50%);
        animation: keep-upright 30s linear infinite;
    }

    @keyframes orbit {
        from {
            transform: translate(-50%, -50%) rotate(0deg);
        }

        to {
            transform: translate(-50%, -50%) rotate(360deg);
        }
    }

    @keyframes keep-upright {
        from {
            transform: translate(-50%, -50%) rotate(0deg);
        }

        to {
            transform: translate(-50%, -50%) rotate(-360deg);
        }
    }

    @media (max-width: 700px) {
        .orbit {
            width: 320px;
            height: 320px;
            left: 50%;
            top: 50%;
        }

        .item {
            --radius: 125px !important;
        }
    }
</style>
