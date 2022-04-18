<template>
	<div>
		<label class="checkbox">
			<input 
				type="checkbox"
				v-model="test.checked"
			>
			<div class="checkbox__checkmark"></div>
		</label>
	</div>
</template>

<script>

export default {
	props: {
		test: Object
	},
	mounted() {
		//this.test[0].checked = true;
		//console.log(this.test)
	}
}
</script>

<style scoped lang="scss">
	.checkbox {
		display: inline-block;
		position: relative;
		cursor: pointer;
		input {
			position: absolute;
			opacity: 0;
			cursor: pointer;
			height: 0;
			width: 0;
			&:checked ~
			.checkbox__checkmark {
				background-color: #f7cb15;
				&:after {
					left: 21px;
				}
			}
		}
		&:hover {
			input {
				& ~ checkbox__checkmark {
					background-color: #eee;
				}
				&:checked ~ checkbox__checkmark {
					background-color: #f7cb15;
				}
			}
		}
		.checkbox__checkmark {
			position: absolute;
			height: 22px;
			width: 40px;
			background-color: #eee;
			transition: background-color 0.25s ease;
			border-radius: 11px;
			&:after {
				content: "";
				position: absolute;
				left: 3px;
				top: 3px;
				width: 16px;
				height: 16px;
				display: block;
				background-color: #fff;
				border-radius: 50%;
				transition: left 0.25s ease;
			}
		}
	}
</style>