<template>
  <div>
    <EventsList :events="eventsList" />
  </div>
</template>

<script>
	import EventsList from './components/EventsList.vue'

	export default {
		components: {
			EventsList
		},
		data() {
			return {
				eventsList: [{
					id: 1,
					title: "Raduno primaverile",
					description: "Bellissimo posto",
					meeting: "Gravesano, 6929",
					date: "14.02.2022"
				},
				{
					id: 2,
					title: "Raduno di natale",
					description: "Parcheggio grande",
					meeting: "Lamone, 6928",
					date: "25.12.2022"
				},
				{
					id: 3,
					title: "Raduno clandestino",
					description: "Parcheggio privato",
					meeting: "Lugano, 6900",
					date: "09.06.2022"
				}]
			}
		}
	}
</script>

<style>
	#app {
		font-family: Avenir, Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;
		color: #2c3e50;
		margin-top: 60px;
	}
</style>