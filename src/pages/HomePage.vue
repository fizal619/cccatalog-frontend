<template>
<div class="home-page grid-container full">
  <header-section showHero="true"></header-section>
  <div class="home-page_body">
    <section class="featured-images">
      <header class="featured-images_header">
        <h2 class="featured-items_title">Top Categories</h2>
      </header>
      <div class="featured-images_inner
                  grid-x
                  grid-margin-x
                  grid-margin-y">
        <div @click="onCategoryClick('people')"
             class="featured-images_item small-6 medium-3 cell">
          <span class="featured-images_banner">People</span>
          <img src="@/assets/people_medium.jpg" alt="">
        </div>
        <div @click="onCategoryClick('nature')"
             class="featured-images_item small-6 medium-3 cell">
          <span class="featured-images_banner">Nature</span>
          <img src="@/assets/nature_medium.jpg" alt="">
        </div>
        <div @click="onCategoryClick('landscapes')"
             class="featured-images_item small-6 medium-3 cell">
          <span class="featured-images_banner">Landscapes</span>
          <img src="@/assets/landscapes_medium.jpg" alt="">
        </div>
        <div @click="onCategoryClick('animals')"
             class="featured-images_item small-6 medium-3 cell">
          <span class="featured-images_banner">Animals</span>
          <img src="@/assets/animals_medium.jpg" alt="">
        </div>
      </div>
    </section>
  <section class="grid top-images">
    <header class="top-images_header">
      <h2 class="featured-items_title">Top Picks</h2>
    </header>
    <div  class="header-grid">
      <figure v-for="(image, index) in images" v-if="index < 4"
           :class="image.class" :key="index"
           @click="onGotoDetailPage(image)">
         <a :href="image.url"
             @click.prevent="() => false"
             target="new">
          <img :src="image.src" />
        </a>
        <figcaption class="grid_item-overlay grid_item-overlay__top">
          <license-icons :image="image"></license-icons>
        </figcaption>
        <figcaption class="grid_item-overlay
                           grid_item-overlay__bottom">
          <div @click.stop="() => false"
               class="grid_overlay-title"
               v-html="image.title"
               target="new"></div>
        </figcaption>
      </figure>
      <div class="bottom-block">
        <figure v-for="(image, index) in images" v-if="index > 3"
             :class="image.class" :key="index"
             @click="onGotoDetailPage(image)">
           <a :href="image.url"
              @click.prevent="() => false"
              target="new">
            <img :src="image.src" />
          </a>
          <figcaption class="grid_item-overlay
                             grid_item-overlay__top">
            <license-icons :image="image"></license-icons>
          </figcaption>
          <figcaption class="grid_item-overlay grid_item-overlay__bottom">
            <div class="grid_overlay-title"
                 target="new"
                 @click.stop="() => false"
                 v-html="image.title"></div>
          </figcaption>
        </figure>
      </div>
    </div>
  </section>
  </div>
  <footer-section></footer-section>
</div>
</template>

<script>
import HeaderSection from '@/components/HeaderSection';
import SearchGrid from '@/components/SearchGrid';
import FooterSection from '@/components/FooterSection';
import LicenseIcons from '@/components/LicenseIcons';
import router from '@/router';

const HomePage = {
  name: 'home-page',
  components: {
    HeaderSection,
    SearchGrid,
    LicenseIcons,
    FooterSection,
  },
  data: () => ({
    images: [
      {
        class: 'grid-item block b1',
        id: '2a4d0a72-0423-4c1e-b30c-1e13fff30bde',
        license: 'by',
        license_version: '2.0',
        src: require('@/assets/pumpkins_medium.jpg'), // eslint-disable-line global-require
        title: '<a href="https://www.flickr.com/photos/greyworld/6253809589">"creepy pumpkins"</a> by <a href="https://www.flickr.com/people/greyworld/">Grey World</a> is licensed under <a href="https://creativecommons.org/licenses/by/2.0" class="photo_license"> CC by 2.0</a>',
        url: 'https://www.flickr.com/photos/greyworld/6253809589',
      }, {
        class: 'grid-item block b2',
        id: '71bc2f24-a231-4f89-a568-6549d7d39f15',
        license: 'by',
        license_version: '2.0',
        src: require('@/assets/halloween-storefront_large.jpg'), // eslint-disable-line global-require
        title: '<a href="https://www.flickr.com/photos/larow/10601605916">"Trick or Treat"</a> by <a href="https://www.flickr.com/people/larow/">Bre LaRow</a> is licensed under <a href="https://creativecommons.org/licenses/by/2.0"> CC BY 2.0 </a>',
        url: 'https://www.flickr.com/photos/larow/10601605916',
      }, {
        class: 'grid-item block b3',
        id: 'f5db1619-7453-49da-8c8d-cb98fbfa849d',
        license: 'by',
        license_version: '2.0',
        src: require('@/assets/halloween_large.jpg'), // eslint-disable-line global-require
        title: '<a href="https://www.flickr.com/photos/gotovan/15390205559/">"Halloween Parade 2014"</a> by <a href="https://www.flickr.com/people/gotovan/">GoToVan</a> is licensed under <a href="https://creativecommons.org/licenses/by/2.0"> CC BY 2.0 </a>',
        url: 'https://www.flickr.com/photos/gotovan/15390205559/',
      }, {
        class: 'grid-item block b4',
        id: '655f2602-bdbc-412e-960a-88b45e2ec797',
        license: 'by-nc',
        license_version: '3.0',
        src: require('@/assets/lanterns.jpg'), // eslint-disable-line global-require
        title: '<a href="https://500px.com//photo/179448237/halloween-comes-to-town-by-andrei-sokolovski">"Halloween Comes to Town"</a> by <a href="null">awesok</a> is licensed under <a href="https://creativecommons.org/licenses/by-nc/3.0"> CC BY-NC 3.0 </a>',
        url: 'https://500px.com/photo/179448237/halloween-comes-to-town-by-andrei-sokolovski',
      },
      {
        class: 'grid-item block b5',
        id: '385dca42-8bbd-4d67-9447-357df93d6d5a',
        license: 'by-nc-nd',
        license_version: '2.0',
        src: require('@/assets/halloween_by_vecvex.jpg'), // eslint-disable-line global-require
        title: '<a href="http://vecvex.deviantart.com/art/Halloween-102174565">"Halloween"</a> by <a href="http://vecvex.deviantart.com/">vecvex</a> is licensed under <a href="https://creativecommons.org/licenses/by-nc-nd/3.0"> CC BY-NC-ND 3.0 </a>',
        url: 'https://www.deviantart.com/vecvex/art/Halloween-102174565',
      },
      {
        class: 'grid-item block b6',
        id: '7b922486-0388-47de-9589-3f8db37e9a65',
        license: 'by',
        license_version: '2.0',
        src: require('@/assets/halloween-decorations.jpg'), // eslint-disable-line global-require
        title: '<a href="https://www.flickr.com/photos/mdid/6343507061">"Halloween decorations"</a> by <a href="https://www.flickr.com/people/mdid/">David Pursehouse</a> is licensed under <a href="https://creativecommons.org/licenses/by/2.0"> CC BY 2.0 </a>',
        url: 'https://www.flickr.com/photos/mdid/6343507061',
      },
      {
        class: 'grid-item block b7',
        id: 'b310a08b-0a9d-4bc4-808b-c532f934e157',
        license: 'by',
        license_version: '2.0',
        src: require('@/assets/haunted-house_medium.jpg'), // eslint-disable-line global-require
        title: '<a href="https://www.flickr.com/photos/_motormouse_/10756725636">"Haunted House"</a> by <a href="https://www.flickr.com/people/_motormouse_/">_TC Photography_</a> is licensed under <a href="https://creativecommons.org/licenses/by/2.0"> CC BY 2.0 </a>',
        url: 'https://www.behance.net/gallery/51974139/Nike-FFF-Retouching',
      },
    ],
  }),
  methods: {
    onCategoryClick(category) {
      router.push({ path: 'search', query: { q: category } });
    },
    onGotoDetailPage(image) {
      this.$router.push(`/photos/${image.id}`);
    },
  },
};

export default HomePage;
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
$gray: #808080;
$highlight: #4ec6cd;
$nav-text-color: $gray;
$vert-seperate: 4rem;

.home-page .nav {
  position: absolute !important;
  background: transparent !important;

  .badge {
   display: none;
  }
}

.home-page_body {

  /* Small only */
  @media screen and (max-width: 39.9375em) {
    margin: 60px 0 30px;
  }
}

.featured-images {
  margin: 30px 0;
  padding: 30px;

  &_header {
    padding-bottom: 10px;
  }

  /* Small only */
  @media screen and (max-width: 39.9375em) {
    padding: 30px 15px;
  }
}


.featured-images_item {
  position: relative;
  cursor: pointer;
  max-height: 140px;
  overflow: hidden;

  img {
    border-radius: 2px;
  }
}

.featured-images_banner {
  background-color: rgba(12, 10, 14, .7);
  color: #fefefe;
  font-weight: 600;
  left: 0;
  padding: 0.5rem;
  position: absolute;
  top: 25%;
  width: 75%;
  z-index: 10;
}

.featured-images_header {
  border-top: 1px solid #e7e8e9;

  h2 {
    margin-bottom: 1.07142857em;
    font-size: .875em;
    font-weight: 600;
    letter-spacing: 1px;
    line-height: 1.25;
    text-transform: uppercase;
    display: inline-block;
    padding-top: .28571429em;
    border-top: 5px solid rgba(29, 31, 39, 0.8);
    margin-top: -3px;
  }
}

.top-images {
  padding: 30px;

  /* Small only */
  @media screen and (max-width: 39.9375em) {
    padding: 15px;
  }
}

.top-images_header {
  border-top: 1px solid #e7e8e9;

  h2 {
    margin-bottom: 1.07142857em;
    font-size: .875em;
    font-weight: 600;
    letter-spacing: 1px;
    line-height: 1.25;
    text-transform: uppercase;
    display: inline-block;
    padding-top: .28571429em;
    border-top: 5px solid rgba(29, 31, 39, 0.8);
    margin-top: -3px;
  }
}

.header-grid {
  width: 100%;
  height: 100vh;
  display: grid;
  grid-template-rows: 1fr 1fr 1fr;
  grid-template-columns: repeat(5, 1fr);
  grid-template-areas:
  "big-top big-top big-top small-top small-top"
  "small-middle small-middle big-middle big-middle big-middle"
  "big-bottom big-bottom big-bottom big-bottom big-bottom";
  margin: 15px 0;

  /* Small only */
  @media screen and (max-width: 39.9375em) {
    display: block;
    height: auto;
  }
}

.grid-item {
  overflow: hidden;

  &:hover .grid_item-overlay {
    opacity: 1;
    bottom: 0;
  }
}

.grid_item-overlay {
  opacity: 0;
  transition: all .4s ease;
  position: absolute;
  width: 100%;
  height: 20%;
  bottom: -100%;
  color: #fff;
  background: linear-gradient(to top, rgba(0,0,0,.5) 0, rgba(0,0,0,0) 100%);
  padding: 10px;

  &__top {
    height: 20px;
    transition: all .5s ease;
    background: linear-gradient(to bottom,
                rgba(0,0,0,.5)
                0,
                rgba(0,0,0,0) 100%);
    top: 0;

    .photo-license-icons {
      height: 20px !important;
    }
  }

  &__bottom {
    height: 30px;
    background: linear-gradient(to top,
                rgba(0,0,0,.5)
                0,
                rgba(0,0,0,0) 100%);
    bottom: -100%;
    top: auto;
  }

  /* Small only */
  @media screen and (max-width: 39.9375em) {
    bottom: 0;
    opacity: 1;
  }
}

.grid_overlay-title {
  position: absolute;
  display: block;
  bottom: 10px;
  left: 10px;
  z-index: 100;
  color: #fff;

  a {
    color: #fff !important;

    &:hover {
      text-decoration: underline;
    }
  }

}

.block {
  position: relative;
  height: 100%;
  width: 100%;
  max-height: 250px;
  overflow: hidden;
  border: 1px solid white;
  background: black;
  opacity: 0.8;
  transition: opacity 0.2s ease-out;
  cursor: pointer;

  &:hover {
    transition: opacity 0.2s ease-in;
    opacity: 1;

  }
}

.block_overlay {
  position: absolute;
  top: 200px;
}

.b1 {
  grid-area: big-top;

}

.b2 {
  grid-area :small-top;
}

.b3 {
  grid-area: small-middle;
}

.b4 {
  grid-area: big-middle;
}

.bottom-block {
  grid-area: big-bottom;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;

  /* Small only */
  @media screen and (max-width: 39.9375em) {
    display: block;
    height: auto;
  }
}
</style>
