<template>
  <footer class="blog-footer">
    <p>Made by <a href="https://github.com/Mitscherlich" target="_blank">Mitscherlich</a> with ❤️ Powered by <a href="https://hexo.io/" title="Hexo">Hexo</a></p>
    <p>Theme 🚧 <a href="https://github.com/Mitscherlich/hexo-theme-amber" target="_blank">Amber</a></p>
    <!-- i18n selector -->
    <b-dropdown :text="$t(locale)" class="mb-2" variant="link">
      <b-dropdown-item @click="locale = 'zh_cn'">{{ $t('zh_cn') }}</b-dropdown-item>
      <b-dropdown-item @click="locale = 'zh_hs'">{{ $t('zh_hs') }}</b-dropdown-item>
      <b-dropdown-item @click="locale = 'en_us'">{{ $t('en_us') }}</b-dropdown-item>
    </b-dropdown>
  </footer>
</template>

<script lang="ts">
import { Component, Watch, Vue } from 'vue-property-decorator';
import store from 'store';

@Component
export default class BFooter extends Vue {
  private locale: string = '';

  private created() {
    this.locale = store.get('locale') || 'zh_cn';
  }

  @Watch('locale')
  private onLocaleChanged(val: string) {
    store.set('locale', val);
    this.$i18n.locale = val;
  }
}
</script>
