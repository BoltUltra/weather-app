<script context="module">
	export async function load({ fetch }) {
		const res = await fetch(
			'https://api.openweathermap.org/data/2.5/weather?lat=11.7594&lon=9.3392&appid=5589aad6bafabc56722198615610216c'
		);
		const data = await res.json();

		if (res.ok) {
			return {
				props: {
					result: data
				}
			};
		}
	}
</script>

<script>
	export let result;
</script>

<div class="weather-app w-1/2 mx-auto text-center">
	<img
		src={`http://openweathermap.org/img/w/${result.weather[0].icon}.png`}
		alt=""
		class="mx-auto w-20"
	/>
	<h1 class="location">{result.name}</h1>
	<h1 class="location">{result.weather[0].main}</h1>
	<p class="description capitalize">{result.weather[0].description}</p>
</div>
