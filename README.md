# Demo1

<!Doctype html>
<html>
    <head>
        <meta charset="UTF-8">
        <title>demopage</title>
        <script src="https://cdn.babylonjs.com/babylon.max.js"></script>

        <script src="babylon.js"></script>
        <script src="babylon.objFileLoader.js"></script>

        <style>
            #canvas {
                width: 100%;
                height: 100%;
            }
        </style>
    </head>
    <body>
        <canvas id="canvas"></canvas>
        <script>
            window.addEventListener("DOMContentLoaded", function() {
                var canvas = document.getElementById("canvas");
                var engine = new BABYLON.Engine(canvas,true);

                var createScene = function () {
                    var scene = new BABYLON.Scene(engine);
                    scene.clearColor = new BABYLON.Color3.White();
                    
                    //var box = BABYLON.Mesh.CreateBox("Box",4.0,scene);//random box showing up
                    var model1 = BABYLON.SceneLoader.ImportMeshAsync("", "", "VE-Stand-PRIM2.obj", scene);//tiktok stand not showing up

                    var camera = new BABYLON.TouchCamera("TouchCamera", new BABYLON.Vector3(0, 0, -10), scene);
                    camera.setTarget(BABYLON.Vector3.Zero());
                    
                    //camera.upperBetaLimit = 0;
                    //camera.lowerRadiusLimit = 0;
                    //camera.upperRadiusLimit = 0;
                    //camera.lowerAlphaLimit = Math.PI / 2;
                    //camera.upperAlphaLimit = Math.PI / 2;
                    //not working for touch camera

                    camera.attachControl(canvas, true); 
                     
                    
                    
                    var light = new BABYLON.PointLight("pointLight", new BABYLON.Vector3(0,10,-10), scene);
                    light.diffuse = new BABYLON.Color3(1,0,0);

                    var layer = new BABYLON.Layer('','https://cdn.nohat.cc/thumb/f/720/ea6442b861be4eab93e8.jpg', scene, true);//background

                    return scene;
                }

                var scene = createScene();



                engine.runRenderLoop(function(){
                    scene.render();
                });
            });
        
        </script>
        
    </body>
    </html> 
