<script context="module" lang="ts">
	import type { Load } from '@sveltejs/kit';

	export const load: Load = async (context) => {
		const res = await fetch(`http://localhost:3000/api/hello`);

		if (res.ok) {
			return {
				status: res.status,
				props: {
					data: await res.json()
				}
			};
		}

		return {
			status: res.status,
			error: new Error(`Could not load /api/hello`)
		};
	};
</script>

<script lang="ts">
	export let data: any;
</script>

<h1>{data.message}</h1>

<style>
</style>
