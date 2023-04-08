<script>
	// @ts-ignore
    import { Canvas, T } from '@threlte/core'
    import { DoubleSide, RepeatWrapping } from 'three';
    import { HTML, OrbitControls, Grid } from '@threlte/extras'

    export let roomSize = 20;
    
    $: roomOffset = roomSize / -2;
</script>

<Canvas >
    <T.PerspectiveCamera
            makeDefault
            position={[roomSize / 3, roomSize / 3, roomSize / 3]}
        >
        <OrbitControls />
    </T.PerspectiveCamera>

    <T.DirectionalLight position={[3, 10, 7]} />
    
    <Grid />

    <!-- Cube -->
    <T.Group scale={roomSize} position={[0, 0.5, roomOffset]} >
        <T.Mesh rotation.y={Math.PI / 2} position.x={-0.5} position.z={0.5} let:ref>
            <T.PlaneGeometry/>
            <T.MeshLambertMaterial
                    side={DoubleSide}
                    args={[
                        {
                            color: 0x3f7b9d,
                        }
                    ]}
                />
        </T.Mesh>
        <T.Mesh let:ref>
            <T.PlaneGeometry  />
            <T.MeshLambertMaterial
                    side={DoubleSide}
                    args={[
                        {
                            color: 0x3f7b9d,
                        }
                    ]}
                />
        </T.Mesh>
        <T.Mesh  rotation.x={-Math.PI / 2} position.y={-0.5} position.z={0.5} let:ref>
            <T.PlaneGeometry  />
            <T.MeshLambertMaterial
                    side={DoubleSide}
                    args={[
                        {
                            color: 0x3f7b9d,
                        }
                    ]}
                />
        </T.Mesh>
    </T.Group>
</Canvas>
