<script lang="ts">
  import { Canvas } from "@threlte/core";
  import Shapes from "./Shapes.svelte";
  </script>
  

  <div id="canvas-container">
    
      <Canvas shadows>
        
          <Shapes/>
      </Canvas>
  </div>
  
  <style>
    #canvas-container {
      width: 100vw;  /* Full width of the viewport */
      height: 70vh; /* Full height of the viewport */
      
   
    }
    

  </style>
  