<!DOCTYPE html>
<html>
  <head>
    <script src="https://aframe.io/releases/1.2.0/aframe.min.js"></script>
    <script src="https://cdn.rawgit.com/jeromeetienne/AR.js/3.3.2/aframe/build/aframe-ar.js"></script>
  </head>

  <body style="margin: 0; overflow: hidden;">
    <a-scene embedded arjs>
      
      <!-- Use built-in Hiro marker -->
      <a-marker id="marker" preset="hiro" emitevents="true">
        <a-entity id="scorecardModel" 
                  gltf-model="School Card_page-0001.glb" 
                  scale="0.5 0.5 0.5" 
                  visible="false">
        </a-entity>
      </a-marker>

      <a-entity camera></a-entity>

      <script>
        const marker = document.querySelector("#marker");
        const model = document.querySelector("#scorecardModel");

        marker.addEventListener("markerFound", () => {
          model.setAttribute("visible", true);
        });

        marker.addEventListener("markerLost", () => {
          console.log("Marker lost, but the model stays visible.");
        });
      </script>

    </a-scene>
  </body>
</html>
