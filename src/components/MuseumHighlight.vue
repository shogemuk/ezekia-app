<template>
	<div class="highlight" :class="[brand, highlight.partner]">
		<img class="highlight__image" :src="highlight.image" />
		<h3 class="highlight__title">
			{{ highlight.name }}
		</h3>
		<p class="highlight__paragraph">{{ highlight.description }}</p>
		<div v-if="highlight.quiz">
			<p><a :href="highlight.news.title" target="_blank">Quiz</a></p>
		</div>
		<button
			type="button"
			class="highlight__button"
			@click.prevent="getNewImage"
		>
			Refresh image
		</button>
	</div>
</template>

<script>
export default {
	name: "MuseumHighlight",
	props: {
		highlight: {
			type: Object,
			required: true,
		},
		brand: {
			type: String,
			required: true,
		},
	},
	methods: {
		getNewImage() {
			//this function will be async assuming it's coming from an api
			const randomNum = Math.floor(Math.random() * 1000);
			this.highlight.image = `https://picsum.photos/394/257?random=${randomNum}`;
		},
	},
	computed: {
		getDate(date) {
			return;
		},
	},
};
</script>

<style lang="scss" scoped>
$observatory_brand_color: #532a52;
$dinosaur_brand_color: #787878;
.highlight {
	position: relative;
	h4 {
		margin: 0 0 10px;
	}
	&__image {
		max-width: 100%;
	}
	&__title {
		color: #2c3791;
		font-size: 24px;
		font-weight: 600;
		margin: 0;
		.observatory & {
			color: $observatory_brand_color;
		}
	}
	&__paragraph {
		color: #808080;
	}
	&__button {
		font-family: inherit;
		border: none;
		background-color: #2a4e53;
		padding: 0.375rem 0.75rem;
		color: #fff;
		border-radius: 5px;
		cursor: pointer;
		.observatory & {
			background-color: $observatory_brand_color;
		}
	}
	&.space {
		&:before {
			content: "";
			position: absolute;
			top: -30px;
			right: -30px;
			background-image: url("/assets/img/star.png");
			background-repeat: no-repeat;
			width: 73px;
			height: 70px;
		}
	}
	&.dinosaur {
		//Example of dinosaur page using font awesome badge
		&:before {
			content: "\f1e5";
			position: absolute;
			top: -30px;
			right: -30px;
			font-family: "FontAwesome";
			text-align: center;
			line-height: 70px;
			border-radius: 50%;
			background-color: $dinosaur_brand_color;
			width: 73px;
			height: 70px;
		}
	}
}
</style>
