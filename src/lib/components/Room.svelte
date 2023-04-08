<script>
    // @ts-ignore
    import { Canvas, T } from '@threlte/core'
    import { DoubleSide, RepeatWrapping } from 'three';
    import { ContactShadows, Float, OrbitControls, Grid, useTexture } from '@threlte/extras';

    import img from '$lib/assets/img/purchase.jpg';

    export let roomSize = 20;
    
    const map = useTexture(img);
    const url = '/lib/assets/models/shoe/scene.gltf';

    $: roomOffset = roomSize / -2;
</script>

<T.PerspectiveCamera
makeDefault
position={[roomSize / 3, roomSize / 3.2, roomSize / 3]}
>
    <OrbitControls />
</T.PerspectiveCamera>

<T.DirectionalLight position={[3, 10, 7]} />

<Float
    floatIntensity={.75}
    floatingRange={[-.5, .5]}
    rotationSpeed={6}
    rotationIntensity={3}
  >
  <ContactShadows frames={1}>
        <T.Mesh >
            <T.BoxGeometry  />
            <T.MeshStandardMaterial
            color="#0059BA"
            />
        </T.Mesh>
    </ContactShadows>
</Float>

<!-- Cube -->
<T.Group scale={roomSize} position={[0, 0.5, roomOffset]} >
    {#await map then value}
        <T.Mesh rotation.y={Math.PI / 2} position.x={-0.5} position.z={0.5} let:ref>
            <T.PlaneGeometry/>
            <T.MeshBasicMaterial 
                map={value}
                side={DoubleSide}
            />
        </T.Mesh>
        <T.Mesh let:ref>
            <T.PlaneGeometry/>
            <T.MeshBasicMaterial 
                map={value}
                side={DoubleSide}
            />
        </T.Mesh>
        <T.Mesh  rotation.x={-Math.PI / 2} position.y={-0.5} position.z={0.5} let:ref>
            <T.PlaneGeometry/>
            <T.MeshBasicMaterial 
                map={value}
                side={DoubleSide}
            />
        </T.Mesh>
    {/await}
</T.Group>