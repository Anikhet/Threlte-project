<script lang="ts">
  import { T as Threlte } from "@threlte/core";
  import * as THREE from "three";
  import { createTransition, Float } from "@threlte/extras";
  import gsap from "gsap";
  import { elasticOut } from "svelte/easing";

  export let position: [number, number, number] = [0, 0, 0];
  export let geometry: THREE.BufferGeometry = new THREE.IcosahedronGeometry(3);
  export let rate = 0.5;

  let visible = true;

  const material = new THREE.MeshStandardMaterial();

  const materialParams = [
    // { color: 0x2ecc71, roughness: 0 },
    // { color: 0xf1c40f, roughness: 0.4 },
    // { color: 0xe74c3c, roughness: 0.1 },
    // { color: 0x8e44ad, roughness: 0.1 },
    // { color: 0x1abc9c, roughness: 0.1 },
    // { color: 0x2980b9, roughness: 0, metalness: 0.5 },
    { color: 0x2c3e50, roughness: 0.1, metalness: 0.5 },
    //  { color: "purple", roughness: 0.1, metalness: 0.5 },
    { color: 0xffd700, roughness: 0.2, metalness: 1 }, // Shiny gold
  { color: 0xc0c0c0, roughness: 0.1, metalness: 1 }, // Polished silver
  { color: 0xb87333, roughness: 0.3, metalness: 0.9 }, // Copper
  { color: 0x00bfff, roughness: 0.1, metalness: 0.8 }, // Glossy sky blue
  { color: 0xff69b4, roughness: 0.05, metalness: 0.9 }, // Hot pink with a shine
  { color: 0x8a2be2, roughness: 0.2, metalness: 0.85 }, // Electric violet
  { color: 0x00ff7f, roughness: 0.15, metalness: 0.7 }, // Shiny spring green
  { color: 0xff4500, roughness: 0.1, metalness: 0.95 }, // Bright shiny red-orange
  { color: 0x4682b4, roughness: 0.05, metalness: 0.85 }, // Steel blue with shine
  { color: 0xadff2f, roughness: 0.1, metalness: 0.8 }, // Green-yellow with a metallic sheen

  ];

  function getRandom() {
    return new THREE.MeshStandardMaterial(gsap.utils.random(materialParams));
  }

  function handleClick(event: MouseEvent) {
    if ("object" in event && event.object instanceof THREE.Mesh) {
      console.log("Event:", event);
      event.object.material = getRandom();
      gsap.to(event.object.rotation, {
        x: `+=2`,
        y: `+=2`,
        z: `+=2`,
        duration: 2,
        ease: "back.out(1,0.3)",
        yoyo: true,
      });
    }
  }

  const bounce = createTransition((ref) => {
  return {
    tick(t) {
      if (t > 0 && !visible) visible = true;
      ref.scale.set(t, t, t);
    },
    easing: elasticOut,
    duration: gsap.utils.random(1200, 1800), // Increased duration
    delay: gsap.utils.random(100, 600), // Adjust delay range
  };
});

</script>

<Threlte.Group position={position.map((p) => p * 2)}>
  <Float
    speed={5 * rate}
    rotationIntensity={6 * rate}
    rotationSpeed={5 * rate}
    floatIntensity={5 * rate}
  >
    <Threlte.Mesh
      {geometry}
      material={getRandom()}
      interactive
      transitions
      on:click={handleClick}
      {visible}
      in={bounce}
    ></Threlte.Mesh>
  </Float>
</Threlte.Group>
