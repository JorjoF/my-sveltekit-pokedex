<script context="module">
    export async function load({page}){
        const id = page.params.id;
        const url = `https://pokeapi.co/api/v2/pokemon/${id}`;
        const res = await fetch(url);
        const pokeman = await res.json();
        return{props: {pokeman}};
    }
</script>
<script>
    export let pokeman;
    const types = pokeman.types.map(type => type.type.name).join(", ");
</script>
<div class="flex flex-col items-center">
<h1 class="text-4xl text-center my-8 uppercase">{pokeman.name}</h1>
<img class="card-image" src={pokeman.sprites['front_default']} alt={pokeman.name}>
<p>Type: <strong>{types}</strong> |  Height: <strong>{pokeman.height}</strong> | Weight: <strong>{pokeman.weight}</strong></p></div>