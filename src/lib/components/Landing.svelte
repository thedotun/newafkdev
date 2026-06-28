<script lang="ts">
    import Orbit from "./Orbit.svelte";
</script>

<div class="landing">
    <div class="overlay"></div>

    <Orbit />

    <div class="avatar"></div>
</div>

<style>
    .landing {
        position: relative;

        width: 100vw;
        height: 100vh;

        display: grid;
        place-items: center;

        overflow: hidden;

        background: url("/background.svg") center center / cover no-repeat;
    }

    .overlay {
        position: absolute;
        inset: 0;

        background: rgba(0, 0, 0, 0.45);
        backdrop-filter: blur(2px);

        z-index: 0;
    }

    .avatar {
        position: absolute;
        z-index: 2;

        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);

        width: 200px;
        height: 200px;

        background: url("/main.svg") center / 117% no-repeat;
        border-radius: 30%;

        border: 3px solid rgba(255, 255, 255, 0.25);

        box-shadow:
            0 0 50px rgba(0, 0, 0, 0.45),
            0 0 30px rgba(255, 255, 255, 0.08);
    }

    @media (max-width: 700px) {
        .avatar {
            width: 160px;
            height: 160px;
        }
    }
</style>
