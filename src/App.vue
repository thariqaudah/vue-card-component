<template>
  <div class="container">
    <ul class="user-list">
      <li class="user-item" v-for="user in users" :key="user.id">
        <Card :user="user" />
      </li>
    </ul>
  </div>
</template>

<script>
import { provide, ref } from 'vue';
import Card from './components/Card.vue';

export default {
  name: 'App',
  components: { Card },
  setup() {
    const users = ref([
      {
        id: 1,
        name: 'Justin Case',
        username: '@justin_case',
        bio: "Hi my developer fellas, I'm Justin and I am a frontend developer. Nice to meet you!",
        avatar: 'justin_case_avatar.jpg',
        cover: 'justin_case_cover.jpg',
        followers: 1300,
        role: 'Programmer',
        isFollowed: false,
      },
      {
        id: 2,
        name: 'Bagus Lazuardi',
        username: '@baguslazuardi',
        bio: "Hello friends. I'm teaching about web development and web design. Let's learn together",
        avatar: 'bagus_lazuardi_avatar.jpg',
        cover: 'bagus_lazuardi_cover.jpg',
        followers: 20000,
        role: 'Teacher',
        isFollowed: true,
      },
      {
        id: 3,
        name: 'Will Barrow',
        username: '@will_barrow',
        bio: "Hi, I'm Will Barrow and I create content about programming and design on Youtube.",
        avatar: 'will_barrow_avatar.jpg',
        cover: 'will_barrow_cover.jpg',
        followers: 120000,
        role: 'Content Creator',
        isFollowed: false,
      },
    ]);

    const handleFollow = userId => {
      console.log(userId);
      users.value = users.value.map(user => {
        if (user.id === userId) {
          user.isFollowed = !user.isFollowed;
        }

        return user;
      });
    };

    provide('handleFollow', handleFollow);

    return {
      users,
    };
  },
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Montserrat', sans-serif;
  font-size: 16px;
  color: #444;
}

#app {
  min-height: 100vh;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 24px;
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
}

.user-list {
  list-style: none;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 24px;

  @media (max-width: 750px) {
    .card {
      max-width: 75%;
      margin: 0 auto;
    }
  }

  @media (max-width: 480px) {
    .card {
      max-width: 100%;
      margin: 0 auto;

      .card-body {
        padding: 0 16px 16px;
      }
    }
  }

  @media (max-width: 350px) {
    .card {
      .card-body {
        .card-title {
          .name {
            font-size: 16px;
          }
          .username {
            font-size: 14px;
          }
        }

        .card-bio {
          font-size: 14px;
        }

        .card-details {
          font-size: 12px;
        }

        .card-socials {
          .social-link {
            width: 26px;
            height: 26px;

            .social-icon {
              width: 20px;
              height: 20px;
            }
          }
        }
      }
    }
  }
}

.btn {
  display: inline-block;
  background-color: transparent;
  color: #444;
  border: none;
  padding: 8px 16px;
  font-size: 16px;
  font-weight: 600;
  border-radius: 100px;
  cursor: pointer;
  transition: all 0.2s ease-in;

  &-primary {
    background-color: #3cd278;
    color: #fff;
    box-shadow: 0px 2px 5px rgba(60, 210, 120, 0.25);

    &:hover {
      background-color: darken($color: #3cd278, $amount: 10);
    }
  }

  &-secondary {
    background-color: #e7e7e7;
    color: #737373;

    &:hover {
      background-color: #fff;
    }
  }
}
</style>
