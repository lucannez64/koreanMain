<template>
  <div>
    <section class="hero is-primary has-text-centered">
      <div class="hero-body">
        <div class="container">
          <h1 class="title">
            Korean Main
          </h1>
          <h2 class="subtitle">
            Le meilleur blog pour apprendre le coréen
          </h2>
        </div>
      </div>
    </section>

    <section class="section">
      <div class="container">
        <div class="columns">
          <div class="column is-three-fifths is-offset-one-fifth">
            <div v-for="post in posts" :key="post.slug" class="box mb-5 ">
              <div>
                <nuxt-link :to="post.slug">
                  <h3 class="hover title is-4">
                    {{ post.title }}
                  </h3>
                  <div class="descrp">
                    {{ post.description }}
                  </div><br>
                  <img :src="require(`~/assets/img/${post.image}.png`)" class="img-article" width="640px" height="320px">
                </nuxt-link>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  async asyncData ({ $content }) {
    const posts = await $content('posts').sortBy('createdAt', 'desc').fetch()

    return { posts }
  }
}
</script>

<style>
  .hover:hover {
    color: #3273dc;
  }
  h3 a {
    color: #363636;
  }
.mb-5{
  width: 660px;
}
  .descrp:hover {
    color: #3273dc;
  }

  .descrp{
    color: #363636;
  }
</style>
