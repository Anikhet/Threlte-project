<script>
  import Scene from "../lib/Hero/Scene.svelte";
</script>

<div
  class="absolute top-0 z-[-2] h-screen w-screen bg-white bg-[radial-gradient(ellipse_80%_80%_at_50%_-20%,rgba(120,119,198,0.3),rgba(255,255,255,0))]"
>
  <div class="flex items-center justify-center flex-col md:flex-row h-full">
    <div class="flex flex-col items-center justify-center absolute top-[25%]">
      <h1 class="font-urbanist font-extrabold md:text-9xl text-5xl">
        Anikhet Mulky
      </h1>
      <h2 class="font-urbanist font-bold md:text-5xl text-2xl">
        Software Developer
      </h2>
    </div>
    <Scene />
  </div>
</div>
