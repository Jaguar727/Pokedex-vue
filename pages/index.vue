<template>
	<div>
		<Header />
		<div class="position-fixed h-100 w-100 top-0 top-25 bg-gradient-ghost" />

		<div class="container pt-92 mt-16">
			<div class="row plr-40">
				<div
					class="col-lg-6 d-flex justify-content-center col-xl-3"
					v-for="(pokemon, index) in pokemons"
					:key="pokemon._id"
					:index="index"
				>
					<Pokemon-Card class="w-100 mb-16" :pokemon="pokemons[index]" />
				</div>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	async asyncData({ $axios }) {
		try {
			const pokemon = await $axios.$get("/api/pokemon");
			return {
				pokemons: pokemon,
			};
		} catch (error) {
			console.log(error);
		}
	},

	methods: {
		listPokemonInConsole(pokemonId) {
			console.log(this.pokemons[pokemonId]);
		},
	},
};
</script>

<style scoped>
.a {
	max-height: 100vh;
}
</style>
