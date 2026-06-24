<script setup>
defineProps({
  ticket: Object,
  isFavourited: Boolean,
});

defineEmits(["toggle-favourite"]);
</script>

<template>
  <div
    class="ticket-card"
    :class="{ featured: ticket.featured, favourited: isFavourited }"
  >
    <div v-if="ticket.featured" class="featured-badge">MOST POPULAR</div>

    <div class="card-header">
      <h3>{{ ticket.tier }}</h3>
      <button
        @click="$emit('toggle-favourite', ticket.id)"
        class="favourite-btn"
        :aria-label="isFavourited ? 'Unfavourite' : 'Favourite'"
      >
        {{ isFavourited ? "★" : "☆" }}
      </button>
    </div>

    <div class="price">
      <span class="currency">R</span>
      <span class="amount">{{ ticket.price }}</span>
    </div>

    <p class="description">{{ ticket.description }}</p>

    <ul class="benefits">
      <li v-for="(benefit, index) in ticket.benefits" :key="index">
        <span class="check">✓</span> {{ benefit }}
      </li>
    </ul>

    <slot name="action">
      <button class="cta-btn" :class="{ 'cta-featured': ticket.featured }">
        Notify Me
      </button>
    </slot>
  </div>
</template>

<style scoped>
.ticket-card {
  background: white;
  border: 2px solid #e7e5e4;
  border-radius: 16px;
  padding: 2rem;
  position: relative;
  transition: all 0.3s ease;
}

.ticket-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 12px 32px rgba(0, 0, 0, 0.1);
}

.ticket-card.featured {
  border: 3px solid #f97316;
  transform: scale(1.05);
  box-shadow: 0 12px 40px rgba(249, 115, 22, 0.25);
}

.ticket-card.featured:hover {
  transform: scale(1.05) translateY(-8px);
}

.featured-badge {
  position: absolute;
  top: -12px;
  left: 50%;
  transform: translateX(-50%);
  background: #f97316;
  color: white;
  padding: 6px 16px;
  border-radius: 20px;
  font-size: 0.75rem;
  font-weight: 700;
  letter-spacing: 0.5px;
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1rem;
}

.card-header h3 {
  font-size: 1.75rem;
  color: #1c1917;
}

.favourite-btn {
  background: none;
  border: none;
  font-size: 1.75rem;
  cursor: pointer;
  color: #d6d3d1;
  transition: all 0.2s ease;
  line-height: 1;
}

.favourite-btn:hover {
  transform: scale(1.2);
}

.ticket-card.favourited .favourite-btn {
  color: #fbbf24;
}

.price {
  margin-bottom: 1rem;
}

.currency {
  font-size: 1.5rem;
  font-weight: 600;
  color: #57534e;
}

.amount {
  font-size: 3rem;
  font-weight: 800;
  color: #1c1917;
}

.description {
  color: #57534e;
  margin-bottom: 1.5rem;
  font-style: italic;
}

.benefits {
  list-style: none;
  margin-bottom: 2rem;
}

.benefits li {
  padding: 0.5rem 0;
  color: #44403c;
  display: flex;
  gap: 0.5rem;
}

.check {
  color: #22c55e;
  font-weight: 700;
}

.cta-btn {
  width: 100%;
  background: #292524;
  color: white;
  border: none;
  padding: 1rem;
  border-radius: 8px;
  font-size: 1rem;
  font-weight: 700;
  cursor: pointer;
  transition: all 0.2s ease;
}

.cta-btn:hover {
  background: #1c1917;
  transform: scale(1.02);
}

.cta-btn.cta-featured {
  background: #f97316;
}

.cta-btn.cta-featured:hover {
  background: #ea580c;
}
</style>
