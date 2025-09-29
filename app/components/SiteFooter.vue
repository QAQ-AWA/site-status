<template>
  <footer id="footer">
    <n-flex class="link" align="center">
      <!-- 只保留 Email 按钮 -->
      <n-button
        :focusable="false"
        quaternary
        circle
        @click="jumpLink(linkData.email)"
      >
        <template #icon>
          <Icon name="icon:email" />
        </template>
      </n-button>
    </n-flex>

    <n-flex :size="4" class="text" align="center" vertical>
      <n-p depth="3">
        Copyright &copy; 2023 - {{ new Date().getFullYear() }}
        <n-text depth="3" @click="jumpLink('https://halfair.top')">
          HalfAir
        </n-text>
        | Powered by SiteStatus
      </n-p>
      <n-p v-if="siteIcp" depth="3">
        <n-text
          depth="3"
          @click="jumpLink('https://beian.miit.gov.cn/')"
        >
          {{ siteIcp }}
        </n-text>
      </n-p>
    </n-flex>
  </footer>
</template>

<script setup lang="ts">
const { public: configPublic } = useRuntimeConfig();
const { siteIcp } = configPublic;

const linkData = {
  email: "mailto:7780102@qq.com",
};

function jumpLink(url: string) {
  if (url) window.open(url, "_blank");
}
</script>

<style lang="scss" scoped>
footer {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px;
  margin-top: auto;
  z-index: 100;
  .link {
    margin-bottom: 8px;
  }
  .text {
    .n-p,
    .n-text {
      margin: 0;
      font-size: 13px;
      line-height: 22px;
    }
    .n-text {
      font-weight: bold;
      cursor: pointer;
      &:hover {
        color: var(--normal-color);
      }
    }
  }
}
</style>
