<template>
  <section class="events" id="events">
    <div class="events--wrapper">
      <p>
        Events: {{ events }}
      </p>
      <div class="events__text">
        <h2 class="events__text__title">
              <span class="events__text__title--span--am">
                MY LIFE
              </span>
          <br class="u-space-desktop">
          <span class="events__text__title--span--dj">
                parties
              </span>
          IS ONE BIG RHYME
        </h2>
      </div>
      <div class="events__text__cta">
        <a class="link-cta" href="https://www.facebook.com/djphazes/" target="_blank">My FB page </a>
      </div>
    </div>

    <div class="events__container">
      <div class="glider-contain">
        <div class="glider">
          <div>
            <div class="glider__card">
              <div class="glider__card__img">
                <img src="@/assets/img/events/BarDenPhazes-min.png" alt="event one">
              </div>
              <p class="glider__card__name">
                Bar Den opening and closing night
                <span class="glider__card__date">
                      7 dec 2019 - 4 jan 2020
                    </span>
              </p>
              <p class="glider__card__text">
                I was honoured to rock the decks on both the opening and closing night, sharing the
                line-up with Faisal and Hush Hefner.
              </p>
            </div>
          </div>

          <div>
            <div class="glider__card">
              <div class="glider__card__img">
                <img src="@/assets/img/events/WolfClubEaglPhazes.jpg" alt="event two">
              </div>
              <p class="glider__card__name">
                Wolf Club invites Eagl
                <span class="glider__card__date">
                      9 nov 19
                    </span>
              </p>
              <p class="glider__card__text">
                One of my highlights was sharing the stage with the one and only Papi Cheagl aka
                Eagl. 

              </p>
            </div>
          </div>

          <div>
            <div class="glider__card">
              <div class="glider__card__img">
                <img src="@/assets/img/events/NielsStuBru2.jpg" alt="event thee">
              </div>
              <p class="glider__card__name">
                Black Mamba invites
                <span class="glider__card__date">
                      26 okt 2019
                    </span>
              </p>
              <p class="glider__card__text">
                I was so hyped to have my mix played on national radio for the first time! This
                one-hour mix is up on my SoundCloud for you to check out.
              </p>

            </div>
          </div>

          <div>
            <div class="glider__card">
              <div class="glider__card__img">
                <img src="@/assets/img/events/PhazesKlubGul.jpg" alt="event four">
              </div>
              <p class="glider__card__name">
                Klub Gul with Hakimm
                <span class="glider__card__date">
                      21 sep 2019
                    </span>
              </p>
              <p class="glider__card__text">
                One of the few closing spots I played so far, on stage right after Hakimm and
                Hyalyte.
              </p>
            </div>
          </div>

          <div>
            <div class="glider__card">
              <div class="glider__card__img">
                <img src="@/assets/img/events/PhazesKontest.jpg" alt="event five">
              </div>
              <p class="glider__card__name">
                Kontest
                <span class="glider__card__date">
                      summer of 2019
                    </span>
              </p>
              <p class="glider__card__text">
                In the summer of 19 I was selected as one of the finalists of Kontest, the first DJ
                contest in Antwerp. Out of more than 100 submissions I got to compete with Cisco FM,
                DC Noises, Tuuren, Wanton,…
              </p>

            </div>
          </div>

          <div>
            <div class="glider__card">
              <div class="glider__card__img">
                <img src="@/assets/img/events/PhazesMambaNights.jpg" alt="event six">
              </div>
              <p class="glider__card__name">
                Mamba Nights
                <span class="glider__card__date">
                      6 sept 2019
                    </span>
              </p>
              <p class="glider__card__text">
                I won my first DJ-contest, for the one and only Black Mamba. My prize: opening the
                festival ‘Mamba Nights’ and appearing on an amazing line-up with Black Mamba, Blu
                Samu, Roedel, Krankk, Youth, Yones, Young Mocro and Mars. 
              </p>
            </div>
          </div>

          <div>
            <div class="glider__card">
              <div class="glider__card__img">
                <img src="@/assets/img/events/phazesbarchapel-1-min.jpg" alt="event seven">
              </div>
              <p class="glider__card__name">
                Bar Chapel opening weekend
                <span class="glider__card__date">
                      			18 jun 2019
                    </span>
              </p>
              <p class="glider__card__text">
                It was my pleasure to drop some beats in one of the cosiest places in Antwerp: Bar
                Chapel. I shared the line-up with Juicy the DJ, Nonkel Guy, DTM Funk
              </p>
            </div>
          </div>

          <div>
            <div class="glider__card">
              <div class="glider__card__img">
                <img src="@/assets/img/events/Phazes3.jpg" alt="event eight">
              </div>
              <p class="glider__card__name">
                Sunrise Festival

                <span class="glider__card__date">
						 28 jun 2019
                    </span>
              </p>
              <p class="glider__card__text">
                The summer of 2019 started with a banger, my first festival. It was amazing and got
                to share the stage with Luminasian and Makasi. </p>
            </div>
          </div>

          <!--Empty div to make glider carousel work -->
          <div>
          </div>
        </div>
      </div>

      <button role="button" aria-label="Previous" class="glider-prev">
        <img src="@/assets/img/arrow-right.svg" alt="Previous">
      </button>
      <button role="button" aria-label="Next" class="glider-next">
        <img src="@/assets/img/arrow-right.svg" alt="Next">
      </button>
    </div>
  </section>
</template>

<style>
</style>


<script>
export default {
  data() {
    return {
      events: []
    }
  },

  async fetch({ $prismic, params, error }) {
    const document = await $prismic.client.query('')
    console.log('doc', document)
    if (document) {
      this.events = document
      return { document }
    } else {
      error({ statusCode: 404, message: 'Page not found' })
    }
  }
}
</script>


