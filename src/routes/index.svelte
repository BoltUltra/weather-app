<script context="module">
	export async function load({ fetch }) {
		const res = await fetch(
			'https://api.openweathermap.org/data/2.5/weather?q=Dutse&appid=5589aad6bafabc56722198615610216c'
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

<div class="flex justify-center items-center h-screen">
	<div class="weather-app px-20 py-14 text-center">
		<img
			src={`http://openweathermap.org/img/w/${result.weather[0].icon}.png`}
			alt=""
			class="mx-auto w-20"
		/>
		<div class="space-y-3 text-white">
			<h1 class="location text-4xl font-bold">{result.name} - {result.sys.country}</h1>
			<h1 class="temp font-light text-xl">
				{result.weather[0].main} - {Math.round(result.main.temp - 273.15)}<sup>o</sup>C
			</h1>
			<p class="description capitalize font-extralight text-lg">{result.weather[0].description}</p>
		</div>
	</div>
</div>
