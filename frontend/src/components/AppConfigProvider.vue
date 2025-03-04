<script setup lang="ts">
import zhCN from "ant-design-vue/es/locale/zh_CN";
import enUS from "ant-design-vue/es/locale/en_US";
import duration from "dayjs/plugin/duration";
import "dayjs/locale/zh-cn";
import "dayjs/locale/en";
import dayjs from "dayjs";
import { ref } from "vue";
import { useAppConfigStore } from "@/stores/useAppConfigStore";
import { theme } from "ant-design-vue";
import { ConfigProvider } from "ant-design-vue";

dayjs.extend(duration);

const { getCurrentLanguage, isDarkTheme } = useAppConfigStore();
const locale = ref(enUS);

// init language with lib
if (getCurrentLanguage().toLowerCase() === "zh_cn") {
  dayjs.locale("zh-cn");
  locale.value = zhCN;
} else {
  dayjs.locale("en-us");
}

const isDarkUI = isDarkTheme();
var appTheme = {
  algorithm: theme.defaultAlgorithm,
  token: {
    fontSizeLG: 14,
    fontSizeSM: 12,
    fontSizeXL: 18
  }
};

const catppuccinTheme = {
  algorithm: theme.darkAlgorithm,
  token: {
    borderRadius: 16,
    colorBgBase: "#1e1e2e",
    colorPrimary: "#b4befe",
    colorError: "#f38ba8",
    colorInfo: "#89b4fa",
    colorSuccess: "#a6e3a1",
    colorWarning: "#f9e2af",
    colorTextBase: "#cdd6f4",

    colorBgContainer: "#1e1e2e",
    colorBorder: "#585b70",
    colorBorderSecondary: "#6c7086",
    borderRadiusLG: 16,
    borderRadiusSM: 8,
    borderRadiusXS: 8,

    button: {
      colorBgContainer: "",
      primaryShadow: "none",
      defaultShadow: "none",
      dangerShadow: "none",
    },
  }
}

if (isDarkUI) {
  appTheme = catppuccinTheme;
}
</script>

<template>
  <ConfigProvider :theme="catppuccinTheme" :locale="locale">
    <slot></slot>
  </ConfigProvider>
</template>
