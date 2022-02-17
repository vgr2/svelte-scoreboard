
<script>
	import Navbar from "./Navbar.svelte";
	import Player from "./Player.svelte";
	import AddPlayer from "./AddPlayer.svelte";

	let name = "Harry";
	let points = 100;
	let showControls = false;
	let users = [
		{
			id: 1,
			name: "John"
		}
	];

	const addPoint = () => {points += 1};
	const removePoint = () => {points -= 1};
	const toggleControls = () => {showControls = !showControls};

	let players = [
		{
			name: "Bob",
			points: 120
		},
		{
			name: "Mark",
			points: 143
		},
		{
			name: "John",
			points: 112
		},
	];

	const addPlayer = (e) => {
		const newPlayer = e.detail;
		players = [...players, newPlayer];
	}

	const deletePlayer = (e) => {

		players = players.filter(player => player.name !== e.detail)
	}
</script>


<Navbar />
<div class="container">
	<AddPlayer on:addplayer={addPlayer} />
	{#if players.lenth === 0}
		<p>No Players</p>
	{:else}
		{#each players as player}
			<Player name={player.name} points={player.points} on:removeplayer={deletePlayer} />
		{/each}
	{/if}
</div>

