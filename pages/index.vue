<script setup lang="ts">
const menu = ref()
const items = ref([
  {
    label: 'Router Link',
    route: '/second',
  },
])

const toggle = (event) => {
  menu.value.toggle(event)
}
</script>

<template>
  <div>
    <Button type="button" label="Show menu" @click="toggle" />

    <Menu ref="menu" :model="items" popup>
      <template #item="{ item, props }">
        <NuxtLink
          v-if="item.route"
          v-slot="{ href, navigate }"
          :to="item.route"
          custom>
          <a v-ripple :href="href" v-bind="props.action" @click="navigate">
            <span :class="item.icon" />
            <span class="ml-2">{{ item.label }}</span>
          </a>
        </NuxtLink>
        <a
          v-else
          v-ripple
          :href="item.url"
          :target="item.target"
          v-bind="props.action">
          <span :class="item.icon" />
          <span class="ml-2">{{ item.label }}</span>
        </a>
      </template>
    </Menu>
  </div>
</template>
