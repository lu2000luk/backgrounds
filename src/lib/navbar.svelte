<script>
    //@ts-nocheck
    import { gsap } from "gsap";
    import { goto } from "$app/navigation";

    let rippleItem;

    function ripple(e) {
        console.log(e);
        goto("../../../")
        createRipple(e);
    }

        function createRipple(event) {
            const button = rippleItem;

            const circle = document.createElement("span");
            const diameter = button.clientHeight;
            const radius = diameter / 2;

            circle.style.width = circle.style.height = `${diameter}px`;
            circle.style.left = `${event.clientX - button.offsetLeft - radius}px`;
            circle.style.top = `${event.clientY - button.offsetTop - radius}px`;
            circle.classList.add("ripple");

            const ripple = button.getElementsByClassName("ripple")[0];

            if (ripple) {
                ripple.remove();
            }

            button.appendChild(circle);
        }
</script>

<!-- svelte-ignore a11y-no-static-element-interactions -->
<!-- svelte-ignore a11y-click-events-have-key-events -->
<div class="flex navv cursor-pointer" bind:this={rippleItem} on:click={ripple}>
    <div class="flex items-center pointer-events-none">
        <img src="../../favicon.png" alt="Backgrounds Logo" width="80px" height="80px" class="p-2" />
        <p class="text-3xl text-white font select-none">Backgrounds</p>
    </div>
    <span class="ripple"></span>
</div>

<div class="divider bg-white w-full h-[2px]"></div>

<style>
    .navv {
        position: relative;
        overflow: hidden;
        outline: 0;
        border: 0;
    }

</style>