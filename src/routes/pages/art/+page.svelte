<script>
	import { Canvas, InteractiveObject, OrbitControls, T } from '@threlte/core'
	import { spring } from 'svelte/motion'
    import { DoubleSide } from 'three';
    import { degToRad } from 'three/src/math/MathUtils'
    import { HTML } from '@threlte/extras'
</script>

<div class="h-full w-full">
	<Canvas linear flat>
        <T.PerspectiveCamera makeDefault position={[10, 10, 10]} fov={24}>
			<OrbitControls maxPolarAngle={degToRad(80)} enableZoom={false} target={{ y: 0.5 }} />
		</T.PerspectiveCamera>

		<T.AmbientLight position={{ y: 1, z: 1 }} />

		<!-- Cube -->
		<T.Group scale={1} >
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
                <HTML>
                    <p class="text-2xl">BUY BUY BUY</p>
                </HTML>
                <!-- <T.MeshLambertMaterial
						side={DoubleSide}
                        args={[
							{
								color: 0x3f7b9d,
							}
						]}
					/> -->
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
</div>

<style>
	div {
		height: 100%;
		width: 100%;
	}
</style>