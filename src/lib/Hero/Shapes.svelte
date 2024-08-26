<script lang="ts">

    import {T as Threlte} from "@threlte/core";
    import * as THREE from "three";
  import Geometry from "./Geometry.svelte";
  import { ContactShadows } from "@threlte/extras";
</script>

<Threlte.PerspectiveCamera 
makeDefault
position={[0,0,20]}
aspect={window.innerWidth / window.innerHeight} 
fov={50} 
near={1}
far={40}



/>


<Threlte.DirectionalLight 
  position={[10, 10, 40]} 
  intensity={5} 
  castShadow 
/>

<ContactShadows position={[0,-3.5,0]}
opacity={0.65}
scale={40}
blur={2}
far={9}></ContactShadows>

<Geometry
rate={0.3}
position={[0,0,0]}
geometry={new THREE.IcosahedronGeometry(3)}

/>

<Geometry
rate={0.4}
position={[1,-0.5,5]}
geometry={new THREE.CapsuleGeometry(0.5,1.6,2,16)}

/>

<Geometry
rate={0.4}
position={[-1.5,-0.75,2]}
geometry={new THREE.BoxGeometry(2, 2, 2, 2, 2, 2)}

/>


<Geometry
rate={0.4}
position={[-1.1,0.75,3]}
geometry={new THREE.TorusGeometry( 1, 0.4, 3, 90 )}

/>


<Geometry
rate={0.4}
position={[1.1,0.75,4]}
geometry={new THREE.SphereGeometry( 1, 12, 20 )}

/>
