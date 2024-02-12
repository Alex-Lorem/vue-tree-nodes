<template>
  <div>
    <ul>
      <li v-for="service in services" :key="service.id">
        {{ service.name }} ({{ service.price }})
        <template v-if="service.node === 1">
          <tree :services="getChildren(service.id)" />
        </template>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Tree',
  props: {
    services: {
      type: Array,
      required: true
    }
  },
  methods: {
    getChildren(parentId) {
      return this.services.filter(service => service.head === parentId);
    }
  }
};
</script>
