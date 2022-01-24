<template>
	<div class="card">
		<div
			role="header"
			class="card-header"
			:style="{
				backgroundImage: 'url(' + require('../assets/img/' + user.cover) + ')',
			}"
		></div>

		<div class="card-body">
			<div class="card-img">
				<img
					:src="require(`../assets/img/${user.avatar}`)"
					alt="User image"
					class="avatar"
				/>
				<div class="is-followed btn btn-primary">
					<img
						src="../assets/icons/user-plus.svg"
						alt="User plus icon"
						class="plus"
					/>
					<span>Follow</span>
				</div>
			</div>

			<div class="card-title">
				<p class="name">{{ user.name }}</p>
				<p class="username">{{ user.username }}</p>
			</div>
			<p class="card-bio">{{ user.bio }}</p>

			<div class="card-details">
				<div class="followers">
					<span>{{ user.followers / 1000 }}k</span>
					<span>Followers</span>
				</div>
				<span class="dot" role="image"></span>
				<div class="role">{{ user.role }}</div>
			</div>

			<div class="card-socials">
				<a href="#" class="social-link">
					<img
						src="../assets/icons/facebook.svg"
						alt="Social icon"
						class="social-icon"
					/>
				</a>
				<a href="#" class="social-link">
					<img
						src="../assets/icons/twitter.svg"
						alt="Social icon"
						class="social-icon"
					/>
				</a>
				<a href="#" class="social-link">
					<img
						src="../assets/icons/instagram.svg"
						alt="Social icon"
						class="social-icon"
					/>
				</a>
				<a href="#" class="social-link">
					<img
						src="../assets/icons/youtube.svg"
						alt="Social icon"
						class="social-icon"
					/>
				</a>
				<a href="#" class="social-link">
					<img
						src="../assets/icons/link.svg"
						alt="Social icon"
						class="social-icon"
					/>
				</a>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: 'UserCard',
	props: ['user'],
};
</script>

<style lang="scss" scoped>
.card {
	max-width: 360px;
	min-width: 220px;
	background: #fff;
	border: 1px solid #e7e7e7;
	border-radius: 8px;
	overflow: hidden;

	.card-header {
		height: 150px;
		background-repeat: no-repeat;
		background-size: cover;
		background-position: center;
	}

	.card-body {
		padding: 0 24px 24px;

		.card-img {
			display: flex;
			align-items: center;
			justify-content: space-between;
			transform: translateY(-50%);
			margin-bottom: -24px;

			.avatar {
				width: 84px;
				height: 84px;
				border-radius: 50%;
				box-shadow: 0 0 0 5px #fff;
			}

			.is-followed {
				display: flex;
				align-items: center;
				gap: 8px;
			}
		}

		.card-title {
			display: flex;
			align-items: center;
			gap: 4px;
			margin-bottom: 16px;

			.name {
				font-size: 18px;
				font-weight: 600;
			}

			.username {
				font-size: 16px;
				color: #949494;
			}
		}

		.card-bio {
			font-size: 16px;
			line-height: 1.5;
		}

		.card-details {
			font-size: 14px;
			margin-top: 24px;
			display: flex;
			align-items: center;
			gap: 16px;

			.followers {
				span:first-child {
					margin-right: 4px;
					font-weight: 700;
				}

				span:last-child {
					font-weight: 600;
				}
			}

			.dot {
				width: 6px;
				height: 6px;
				background-color: #e7e7e7;
				border-radius: 50%;
			}

			.role {
				font-weight: 600;
			}
		}

		.card-socials {
			margin-top: 16px;
			display: flex;
			gap: 12px;

			.social-link {
				display: inline-block;
				width: 32px;
				height: 32px;
				display: flex;
				justify-content: center;
				align-items: center;
				border-radius: 50%;
				background-color: #e7e7e7;
				cursor: pointer;
				transition: all 0.2s ease-in;

				&:hover {
					background-color: #c7c7c7;
				}
			}
		}
	}
}
</style>
