<template>
  <div class="secondary-content secondary-content--case">
    <div class="pagination">{{ currentIndex + 1 }} / {{ cases.length }}</div>
    <component :is="$route.params.case" transition="fade" transition-mode="out-in" keep-alive></component>
  </div>
</template>

<script>
import {
  getSecondary,
  getCases,
  getCurrentCase
} from 'vuex/getters';

import Radio24syv from './cases/radio24syv';
import Skagen from './cases/skagen';
import Happyarabia from './cases/happyarabia';
import Terriblechristmas from './cases/terriblechristmas';

export default {
  vuex: {
    getters: {
      secondary: getSecondary,
      cases: getCases,
      currentIndex: getCurrentCase
    }
  },

  route: {
    canDeactivate: function ({ next }) {
      TweenLite.to(this.$el, 0.3, {
        opacity: 0,
        onComplete: () => {
          next();
        }
      });
    }
  },

  components: {
    Radio24syv,
    Skagen,
    Terriblechristmas,
    Happyarabia
  }
};
</script>
