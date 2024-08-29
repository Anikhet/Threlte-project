<script>
  import Scene from "../lib/Hero/Scene.svelte";
  import { onMount } from "svelte";
  import gsap from "gsap";

  onMount(() => {
    const timeline = gsap.timeline();

    // Animate the main heading
    timeline.from(".heading-main", {
      y: 100, // Start from below
      scale: 0.8, // Start smaller
      opacity: 0, // Start invisible
      rotation: -10, // Start rotated
      duration: 1.5, // Longer duration for dramatic effect
      ease: "elastic.out(1, 0.75)", // Elastic effect for bounce
    });

    // Animate the subheading
    timeline.from(".heading-sub", {
      y: 50,
      scale: 0.8,
      opacity: 0,
      rotation: 10,
      duration: 1.2,
      ease: "elastic.out(1, 0.75)",
    }, "-=1"); // Overlap slightly with the previous animation

    // Animate the scene with a pop and spin effect
    gsap.from(".scene-container", {
      scale: 0.5, // Start smaller
      opacity: 0,
      rotation: 360, // Full rotation for a dramatic spin
      duration: 2, // Duration for a smooth entrance
      ease: "back.out(1.7)", // Back easing for a strong pop effect
      delay: 0.2, // Start slightly after the text animations
    });
  });
</script>

<div
  class="absolute top-0 z-[-2] h-screen w-screen bg-white bg-[radial-gradient(ellipse_80%_80%_at_50%_-20%,rgba(120,119,198,0.3),rgba(255,255,255,0))]"
>
  <div class="flex items-center justify-center flex-col md:flex-row h-full w-full">
    <div class="flex flex-col items-center w-[80vw] md:gap-10 absolute md:static top-[25%]">
      <h1 class="font-urbanist font-extrabold md:text-8xl text-5xl text-center heading-main">
        Anikhet Mulky
      </h1>

      <h2 class="font-urbanist font-bold md:text-4xl text-2xl heading-sub">
        Software Developer
      </h2>
    </div>
   
      <Scene />
    
  </div>
</div>

<style>
  /* Optional custom styles for tweaking animation impact */
  .scene-container {
    transform-origin: center; /* Ensures rotation happens centrally */
  }
</style>
