<template>
<v-layout>
  <div class="wrapper">
    <parallax class="section page-header header-filter" :style="headerStyle"></parallax>
    <div class="main main-raised">
      <div class="container">
        <div class="md-layout md-size-18 fix-content">
          <div class="md-layout-item mx-auto">
            <h1 class="title" style="font-size: 36px;">Categorias do mini-curso</h1>
          </div>
          <div class="md-layout-item md-size-100 ">
            <ul v-for="item in getCategories" :key="item.id" v-if="item.hasMiniCourse === true">
              <h3 style="margin-left: -4vh;" > {{ item.label }} </h3>
              <li v-for="categorie in item.categorias" :key="categorie.id" v-if="categorie.miniCourse === true">
                {{ categorie.name }} <span v-if="categorie.ruleContent != ''"> - <a :href='categorie.ruleContent' target='_blank'>Regras</a></span>
              </li>
            </ul>
            <!--Change Url-->
            <br><h4>Regras Gerais <a href='/rules/geral_rules.pdf' target='_blank'>clique aqui.</a></h4>
          </div>
        </div>
      </div>
    </div>
  </div>
</v-layout>
</template>

<script>
import VLayout from '@/layout/MiniCourseLanding.vue';
import { CATEGORY_JSON } from '@/config.js'

export default {
  components: {
    VLayout,
  },
  data () {
    return {
    }
  },
  bodyClass: 'categories-page',
  props: {
    header: {
      type: String,
      default: require('@/assets/img/hero/img2.jpg')
    }
  },
  computed: {
    headerStyle() {
      return {
        backgroundImage: `url(${this.header})`
      };
    },
    getCategories() {
      return CATEGORY_JSON;
    }
  },
   methods: {
  },
};
</script>

<style lang="scss" scoped>
.fix-content {
  width: 100% !important;
  margin-left: 0px !important;
}

.md-ripple > span {
  position: relative;
}

.page-header {
  height: 38vh !important;
}
</style>
