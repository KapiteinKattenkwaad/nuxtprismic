<template>
  <section class="home">
    <p>
      Home
    </p>
    <article>
      <div class="blog-avatar" :style="{ backgroundImage: 'url(' + image + ')' }" ></div>
      <!-- Template for page title -->
      <h1 class="blog-title">
        {{ $prismic.asText(homepageContent.headline) }}
      </h1>
      <!-- Template for page description -->
      <p class="blog-description">{{ $prismic.asText(homepageContent.description) }}</p>

      <!-- Check events exist -->
      <div v-if="events.length !== 0" class="blog-main">
        <!-- Template for events posts -->
        <section v-for="event in events" :key="events.id" v-bind:event="event" class="event">
          <!-- Here :post="post" passes the data to the component -->
          <event-widget :event="event"></event-widget>
        </section>
      </div>
      <!-- If no blog posts return message -->
      <div v-else class="blog-main">
        <p>No events published at this time.</p>
      </div>


      <!-- Check blog posts exist -->
      <div v-if="posts.length !== 0" class="blog-main">
        <!-- Template for blog posts -->
        <section v-for="post in posts" :key="post.id" v-bind:post="post" class="blog-post">
          <!-- Here :post="post" passes the data to the component -->
          <blog-widget :post="post"></blog-widget>
        </section>
      </div>
      <!-- If no blog posts return message -->
      <div v-else class="blog-main">
        <p>No Posts published at this time.</p>
      </div>
    </article>

    <div class="site-wrapper">
      <TheHeader>
      </TheHeader>
      <main class="main" role="main">
        <TopSection>
        </TopSection>
        <TurnOn>
        </TurnOn>
        <MixesSection>
        </MixesSection>
        <ShakeAss>
        </ShakeAss>
        <EventsSection>
        </EventsSection>
        <TheForm>
        </TheForm>
      </main>

      <BottomPicture>
      </BottomPicture>
      <BottomSection>
      </BottomSection>

    </div>

  </section>
</template>

<script>
// Importing blog posts widget
import BlogWidget from '~/components/BlogWidget.vue'
import EventWidget from '~/components/EventWidget.vue'
import TheHeader from "~/components/TheHeader";
import TopSection from "~/components/TopSection";
import TurnOn from "~/components/TurnOn";
import MixesSection from "~/components/MixesSection";
import ShakeAss from "~/components/ShakeAss";
import EventsSection from "~/components/EventsSection";
import TheForm from "~/components/TheForm";
import BottomPicture from "~/components/BottomPicture";
import BottomSection from "~/components/BottomSection";

export default {
  name: 'Home',
  components: {
    BlogWidget,
    EventWidget,
    BottomSection,
    BottomPicture,
    TheForm,
    EventsSection,
    ShakeAss,
    MixesSection,
    TurnOn,
    TopSection,
    TheHeader
  },
  head () {
    return {
      title: 'Prismic Nuxt.js Blog',
    }
  },
  async asyncData({ $prismic, error }) {
    try{
      // Query to get blog home content
      const homepageContent = (await $prismic.api.getSingle('blog_home')).data

      console.log('home', homepageContent)

      // Query to get posts content to preview
      const blogPosts = await $prismic.api.query(
        $prismic.predicates.at("document.type", "post"),
        { orderings : '[my.post.date desc]' }
      )

      // Query to get posts content to preview
      const events = await $prismic.api.query(
        $prismic.predicates.at("document.type", "events"),
        { orderings : '[my.event.date desc]' }
      )

      console.log('events', events)

      // Returns data to be used in template
      return {
        homepageContent,
        posts: blogPosts.results,
        events: events.results,
        image: homepageContent.image.url,
      }
    } catch (e) {
      // Returns error page
      error({ statusCode: 404, message: 'Page not found' })
    }
  },
}
</script>

<style lang="sass" scoped>
</style>
