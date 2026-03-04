<script lang="ts">
    import { haptic, useHaptic, isSupported } from "svelte-attach-haptic";

    const tap = useHaptic("medium", ["pointerdown"]);
</script>

<section>
    <label class="support-indicator">
        <input type="checkbox" checked={isSupported} disabled />
        Vibrate API available
    </label>
    <button {@attach haptic()}>Default (medium on click)</button>
    <button {@attach haptic({ pattern: "success" })}>Success</button>
    <button {@attach haptic({ pattern: "error" })}>Error</button>
    <button {@attach haptic({ pattern: "heavy", events: ["pointerdown"] })}
        >Heavy (on pointerdown)</button
    >
    <button {@attach tap()}>Factory (medium on pointerdown)</button>
    <button {@attach tap({ pattern: "light" })}>Factory override (light)</button
    >
</section>

<style>
    section {
        display: grid;
        place-content: center;

        height: 90svh;
    }

    button {
        margin: 1rem;
        padding: 1rem;
    }

    .support-indicator {
        display: flex;
        align-items: center;
        gap: 0.5rem;
        margin-bottom: 1rem;
        cursor: default;
    }
</style>
