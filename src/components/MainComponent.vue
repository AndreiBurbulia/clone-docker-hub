<template>
  <div class="container">
    <!-- <ContentComponent></ContentComponent> -->
    <div class="homepage">
      <!-- Content -->
      <div class="content">
        <div class="stories">
          <div class="story" v-for="storia in stories" :key="storia.id">
            <img :src="storia.profile_picture" />
            <span>{{ storia.profile_name }}</span>
          </div>
        </div>

        <div class="posts">
          <div class="post" v-for="post in posts" :key="post.id">
            <!-- Post Title -->
            <div class="title_post">
              <div class="left">
                <img alt="Vue logo" :src="post.profile_picture" />
                <span
                  ><strong>{{ post.profile_fullname }}</strong></span
                >
              </div>
              <div class="right">
                <i class="fas fa-ellipsis-h"></i>
              </div>
            </div>
            <!-- Post image -->
            <img alt="Vue logo" :src="post.post_image" />
            <!-- Post details -->
            <div class="post_details">
              <!-- reaction -->
              <div class="reaction">
                <i class="far fa-heart"></i>
                <i class="far fa-comment"></i>
              </div>

              <!-- person -->
              <div class="person">
                <img alt="Vue logo" :src="post.profile_picture" />
                <!-- <i class="fas fa-user-circle"></i> -->
                <span>
                  Piace a <strong>{{ post.likes[0].username }}</strong> e
                  <strong>{{ post.likes.length }} altri</strong></span
                >
              </div>

              <!-- commenti -->

              <!-- <div class="commenti">
                
                <span
                  v-for="comment in getComments(post.comments)"
                  :key="comment.id"
                  ><strong>{{ comment.username }}</strong>
                  {{ comment.text }}</span
                >
                <span
                  v-if="post.comments.length >= 3"
                  @click="getAllComments(index)"
                >
                  Mostra tutti e {{ post.comments.length }} i commenti
                </span>
              </div> -->
              <!-- {{ addVariable(post) }} -->
              <div class="commenti">
                <span
                  v-if="post.comments.length >= 3"
                  @click="getAllComments()"
                >
                  Mostra tutti e {{ post.comments.length }} i commenti
                </span>
                <span
                  v-for="comment in getComments(post.comments, allComments)"
                  :key="comment.id"
                  ><strong>{{ comment.username }}</strong>
                  {{ comment.text }}</span
                >
              </div>

              <!-- orario -->
              <div class="orario">
                <span>{{ tempo(post.date.date) }} Ore fa</span>
              </div>
            </div>
            <!-- aggiungi commento -->
            <div class="add_comment">
              <span>Aggiungi un commento</span>
              <span>Pubblica</span>
            </div>
          </div>
        </div>
      </div>

      <!-- suggestion -->
      <div class="suggestions">
        <!-- profilo -->
        <div class="profile">
          <img alt="Vue logo" src="@/assets/profile.jpg" />
          <div>
            <span><strong> andreiburbulia1</strong></span>
            <span>Andrei Burbulia1</span>
          </div>
          <span>Passa a </span>
        </div>

        <!-- suggerimenti -->
        <div class="sugg">
          <div class="top">
            <span>Suggerimenti per te</span>
            <span> <strong>Mostra tutto</strong> </span>
          </div>

          <div class="middle">
            <div class="card" v-for="storia in stories" :key="storia.id">
              <div class="left">
                <img alt="Vue logo" :src="storia.profile_picture" />
                <span>
                  <strong>{{ storia.profile_name }}</strong>
                </span>
              </div>
              <div class="right">
                <span>Segui</span>
              </div>
            </div>
          </div>

          <div class="bottom">
            <span>
              <i class="far fa-copyright"></i> 2021 INSTAGRAM FROM
              FACEBOOK</span
            >
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Axios from "axios";
export default {
  name: "MainComponent",

  components: {
    // ContentComponent,
  },
  data() {
    return {
      stories: [],
      posts: [],
      allComments: false,
    };
  },

  methods: {
    storiesData() {
      Axios.get("https://flynn.boolean.careers/exercises/api/boolgram/profiles")
        .then((resp) => {
          this.stories = resp.data;
        })
        .catch((e) => {
          console.error(e);
        });
    },

    async postsData() {
      await Axios.get(
        "https://flynn.boolean.careers/exercises/api/boolgram/posts"
      )
        .then((resp) => {
          this.posts = resp.data;
          console.log(this.posts);
        })
        .catch((e) => {
          console.error(e);
        });
    },

    tempo(date) {
      let ora = new Date(date);
      let ora_now = new Date();
      const milliseconds = Math.abs(ora - ora_now);
      const hours = milliseconds / 36e5;
      return hours.toFixed(0);
    },
    getComments(array) {
      if (this.allComments) {
        return array;
      } else {
        return array.slice(0, 3);
      }
    },
    getAllComments() {
      this.allComments = true;
    },
  },

  mounted() {
    this.storiesData();
    this.postsData();
    // setTimeout(() => {
    // }, 2000);
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.homepage {
  margin-top: 2rem;
  display: flex;
  justify-content: space-between;

  .content {
    width: 60%;
    .stories {
      border: 1px solid rgba(0, 0, 0, 0.3);
      border-radius: 0.5rem;
      padding: 1.5rem;
      display: flex;
      overflow-x: hidden;
      .story {
        display: flex;
        flex-direction: column;
        justify-content: center;
        margin-right: 1rem;
        width: 70px;
        img {
          height: 60px;
          width: 60px;
          border-radius: 50%;
          padding: 2px;
          border: 3px solid red;
        }
        span {
          padding-top: 0.5rem;
          white-space: nowrap;
          overflow: hidden;
          text-overflow: ellipsis;
        }
      }
    }

    .posts {
      .post {
        border: 1px solid rgba(0, 0, 0, 0.3);
        border-radius: 0.25rem;
        margin: 2rem 0;

        .title_post {
          display: flex;
          justify-content: space-between;
          align-items: center;
          padding: 1rem;
          .left {
            display: flex;
            align-items: center;
            img {
              height: 30px;
              width: 30px;
              border-radius: 50%;
              margin-right: 0.7rem;
              padding: 2px;
              border: 3px solid red;
            }
          }
        }

        img {
          width: 100%;
        }

        .post_details {
          padding: 1rem;
          display: flex;
          flex-direction: column;
          align-items: flex-start;

          .reaction {
            font-size: 1.5rem;
            i {
              margin-right: 1rem;
            }
          }

          .person {
            margin: 0.5rem 0;
            display: flex;
            align-items: center;
            img {
              height: 25px;
              width: 25px;
              border-radius: 50%;
              margin-right: 1rem;
            }
          }
          .commenti {
            display: flex;
            flex-direction: column;
            align-items: flex-start;
            margin: 1rem 0;
            span {
              padding: 0.25rem 0;
            }
          }

          .orario {
            span {
              font-size: 0.9rem;
              font-weight: bold;
              color: rgba(0, 0, 0, 0.5);
            }
          }
        }
        .add_comment {
          padding: 1rem 0.5rem;
          border-top: 1px solid rgba(0, 0, 0, 0.2);
          display: flex;
          justify-content: space-between;

          span:nth-child(1) {
            color: rgba(0, 0, 0, 0.5);
          }
          span:nth-child(2) {
            font-weight: bold;
            color: rgba(5, 5, 255, 0.8);
          }
        }
      }
    }
  }

  .suggestions {
    width: 40%;
    padding: 1rem;

    .profile {
      display: flex;
      justify-content: space-around;
      align-items: center;
      img {
        height: 50px;
        width: 50px;
        border-radius: 50%;
      }
      & > div {
        span {
          display: block;
        }
        span:nth-child(2) {
          padding-top: 0.25rem;
          color: rgba(0, 0, 0, 0.438);
        }
      }

      & > span {
        font-weight: bold;
        color: rgba(5, 5, 255, 0.8);
      }
    }

    .sugg {
      margin-top: 3rem;
      padding: 1rem;
      .top {
        display: flex;
        justify-content: space-between;
        margin-bottom: 1rem;
        span:first-child {
          font-weight: bold;
          color: rgba(0, 0, 0, 0.507);
        }
      }

      .middle {
        .card {
          padding: 0.5rem 0;
          display: flex;
          justify-content: space-between;
          .left {
            display: flex;
            align-items: center;
            img {
              margin-right: 1rem;
              height: 40px;
              width: 40px;
              border-radius: 50%;
            }
          }
          .right {
            span {
              font-weight: bold;
              color: rgba(5, 5, 255, 0.8);
              padding: 0.5rem 1rem;
              border-radius: 0.25rem;
              border: 1px solid rgba(5, 5, 255, 0.8);

              &:hover {
                background-color: rgba(5, 5, 255, 0.8);
                color: white;
              }
            }
          }
        }
      }

      .bottom {
        margin-top: 1rem;
        span {
          font-size: 0.8rem;
          color: rgba(0, 0, 0, 0.376);
        }
      }
    }
  }
}
</style>
