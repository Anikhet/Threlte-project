<script lang="ts">
  import { onMount } from "svelte";
  import { T as Threlte } from "@threlte/core";
  import * as THREE from "three";
  import Geometry from "./Geometry.svelte";
  import {
    ContactShadows,
    Environment,
    interactivity,
    transitions,
  } from "@threlte/extras";

  let isMobile = false;

  onMount(() => {
    isMobile = /Mobi|Android/i.test(navigator.userAgent);
  });

  interactivity();
  transitions();
</script>

<Threlte.PerspectiveCamera
  makeDefault
  position={[0, 0, isMobile ? 30 : 20]}
  aspect={window.innerWidth / window.innerHeight}
  fov={isMobile ? 60 : 50}
  near={1}
  far={40}
/>

{#if isMobile}
  <Threlte.DirectionalLight 
    position={[10, 10, 20]} 
    intensity={25}
    castShadow 
  />

  <ContactShadows
    position={[0, -3, 0]}
    opacity={0.5}
    scale={20}
    blur={1}
    far={6}
  ></ContactShadows>

{:else}
  <Environment files="smallroom.hdr" path="/" format="hdr" />

  <ContactShadows
    position={[0, -3.5, 0]}
    opacity={0.65}
    scale={40}
    blur={2}
    far={9}
  ></ContactShadows>
{/if}

<Geometry
  rate={0.3}
  position={[0, 0, 0]}
  geometry={new THREE.IcosahedronGeometry(3)}
/>

<Geometry
  rate={0.4}
  position={[1, -0.5, 5]}
  geometry={new THREE.CapsuleGeometry(0.5, 1.6, 2, 16)}
/>

<Geometry
  rate={0.4}
  position={[-1.5, -0.75, 2]}
  geometry={new THREE.CylinderGeometry(1, 1, 3, 550)}
/>

<Geometry
  rate={0.4}
  position={[-1.1, 0.75, 3]}
  geometry={new THREE.TorusGeometry(1, 0.4, 3, 90)}
/>

<Geometry
  rate={0.4}
  position={[1.1, 0.75, 4]}
  geometry={new THREE.SphereGeometry(1, 12, 20)}
/>