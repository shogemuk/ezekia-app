<template>
	<div class="space-page">
		<h1>Space</h1>
		<section class="space-page__highlights">
			<museum-highlight
				v-for="highlight in spaceHighlights"
				:highlight="highlight"
				:key="highlight.id"
				:brand="brandName"
			></museum-highlight>
		</section>
	</div>
</template>

<script>
import MuseumHighlight from "@/components/MuseumHighlight.vue";

export default {
	name: "SpacePage",
	components: {
		MuseumHighlight,
	},
	mixins: [],
	props: {},
	data() {
		return {
			brandName: "space",
			spaceHighlights: [
				{
					date: "2020-04-20 12:20:00",
					description:
						"Asteroids are minor planets, especially of the inner Solar System. Larger asteroids have also been called planetoids.",
					id: 1,
					image: "",
					name: "Asteroids",
				},
				{
					date: "2020-05-20 15:50:00",
					description:
						"A comet is an icy, small Solar System body that, when passing close to the Sun, warms and begins to release gases, a process called outgassing.",
					id: 9,
					image: "",
					name: "Comets",
				},
				{
					date: "2020-05-01 9:22:00",
					description:
						"The term planet is ancient, with ties to history, astrology, science, mythology, and religion.",
					id: 7,
					image: "",
					name: "Planets",
					news: {
						date: "2020-08-18 18:00:00",
						title: "Attend our talk about Jupiter with Dr. Hogarth",
					},
					quiz: "https://planetquiz.space",
				},
				{
					date: "2020-07-05 4:10:00",
					description:
						"A meteor shower is a celestial event in which a number of meteors are observed to radiate, or originate, from one point in the night sky.",
					id: 12,
					image: "",
					name: "Meteor showers",
					news: {
						title: "The Lyrids will peak at on April 21-22 2021, at night",
					},
				},
			],
			spacePartners: {
				observatory: {
					createdAt: "2020-06-01 11:45:00",
					info: "The Mauna Kea Observatories (MKO) are a number of independent astronomical research facilities and large telescope observatories that are located at the summit of Mauna Kea on the Big Island of Hawaiʻi, United States.",
					image: "",
					name: "Mauna Kea Observatories",
				},
			},
		};
	},
	computed: {},
	methods: {
		mergeData() {
			Object.keys(this.spacePartners).map((obj) => {
				const date = this.spacePartners[obj].createdAt;
				const description = this.spacePartners[obj].info;
				const id = Math.floor(Math.random() * 1000000);
				const name = this.spacePartners[obj].name;
				const partner = obj;
				this.spaceHighlights.push({
					date,
					description,
					id,
					name,
					partner,
				});
			});
			this.spaceHighlights.forEach((item) => {
				const randomNum = Math.floor(Math.random() * 1000);
				item.image = `https://picsum.photos/394/257?random=${randomNum}`;
			});
			this.spaceHighlights.sort(
				(a, b) => new Date(a.date) - new Date(b.date)
			);
		},
	},
	created() {
		this.mergeData();
	},
};
</script>

<style lang="scss" scoped>
.space-page {
	margin-bottom: 2rem;
	h1 {
		padding-top: 2rem;
		padding-bottom: 2rem;
	}
	margin-left: auto;
	margin-right: auto;
	@media (min-width: 1536px) {
		max-width: 1536px;
	}
	&__highlights {
		display: grid;
		grid-template-columns: repeat(4, 1fr);
		grid-template-rows: 1fr 1fr;
		gap: 63px;
	}
}
</style>
