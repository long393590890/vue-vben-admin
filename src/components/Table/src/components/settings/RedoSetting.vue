<template>
  <Tooltip placement="top">
    <template #title>
      <span>{{ t('component.table.settingRedo') }}</span>
    </template>
    <RedoOutlined @click="redo" />
  </Tooltip>
</template>
<script lang="ts">
  import { defineComponent } from 'vue';
  import { useTableContext } from '../../hooks/useTableContext';
  import { Tooltip } from 'ant-design-vue';
  import { RedoOutlined } from '@ant-design/icons-vue';
  import { useI18n } from '/@/hooks/web/useI18n';

  export default defineComponent({
    name: 'RedoSetting',
    components: {
      RedoOutlined,
      Tooltip,
    },

    setup() {
      const table = useTableContext();
      const { t } = useI18n();

      function redo() {
        table.reload();
      }

      return {
        redo,
        t,
      };
    },
  });
</script>
