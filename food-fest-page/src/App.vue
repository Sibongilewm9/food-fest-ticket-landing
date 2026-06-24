<script setup>
import { ref } from "vue";
import TicketCard from "./components/TicketCard.vue";

const favourites = ref([]);

const tickets = ref([
  {
    id: 1,
    tier: "Bronze",
    price: 250,
    description: "Perfect for casual foodies",
    benefits: [
      "General festival entry",
      "Access to 20+ food stalls",
      "Free water stations",
    ],
    featured: false,
  },
  {
    id: 2,
    tier: "Silver",
    price: 550,
    description: "Our most popular choice",
    benefits: [
      "All Bronze benefits",
      "Fast-track entry lane",
      "2x free drink vouchers",
      "Access to cooking demos",
    ],
    featured: true,
  },
  {
    id: 3,
    tier: "Gold",
    price: 1050,
    description: "The ultimate VIP experience",
    benefits: [
      "All Silver benefits",
      "VIP lounge access",
      "Meet & greet with chefs",
      "Exclusive tasting menu",
      "Front row for live music",
    ],
    featured: false,
  },
]);

const toggleFavourite = (ticketId) => {
  const index = favourites.value.indexOf(ticketId);
  if (index > -1) {
    favourites.value.splice(index, 1);
  } else {
    favourites.value.push(ticketId);
  }
};
</script>

<template>
  <div class="app">
    <header class="hero">
      <div class="hero-content">
        <h1>Cape Town Food Fest 2026</h1>
        <p>A weekend of chefs, street food, music & community vibes</p>
        <p class="event-date">15 - 17 September 2026 | Green Point Park</p>
      </div>
    </header>

    <main class="container">
      <section class="tickets-section">
        <h2>Choose Your Ticket</h2>
        <p class="subtitle">
          All tiers include festival entry. Pick the experience you want.
        </p>

        <div class="tickets-grid">
          <TicketCard
            v-for="ticket in tickets"
            :key="ticket.id"
            :ticket="ticket"
            :is-favourited="favourites.includes(ticket.id)"
            @toggle-favourite="toggleFavourite"
          />
        </div>
      </section>

      <div v-if="favourites.length > 0" class="favourites-bar">
        <span
          >★ You favourited {{ favourites.length }}
          {{ favourites.length === 1 ? "tier" : "tiers" }}</span
        >
      </div>
    </main>

    <footer class="footer">
      <p>© 2026 Cape Town Food Fest. Tickets coming soon.</p>
    </footer>
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "Inter", "Segoe UI", sans-serif;
  background: #000000;
  color: #ffffff;
}

.hero {
  background: linear-gradient(135deg, #f97316 0%, #ea580c 100%);
  color: white;
  padding: 4rem 2rem;
  text-align: center;
  width: 100%;
}

.hero-content h1 {
  font-size: 3rem;
  margin-bottom: 1rem;
  font-weight: 800;
}

.hero-content p {
  font-size: 1.25rem;
  opacity: 0.95;
}

.event-date {
  margin-top: 1rem;
  font-weight: 600;
  background: rgba(255, 255, 255, 0.2);
  display: inline-block;
  padding: 0.5rem 1rem;
  border-radius: 20px;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 4rem 2rem;
}

.tickets-section h2 {
  font-size: 2.5rem;
  text-align: center;
  margin-bottom: 0.5rem;
  color: #f5f5f5;
}

.subtitle {
  text-align: center;
  color: #ffffff;
  margin-bottom: 3rem;
  font-size: 1.1rem;
}

.tickets-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  align-items: start;
}

.favourites-bar {
  position: fixed;
  bottom: 2rem;
  left: 50%;
  transform: translateX(-50%);
  background: #1c1917;
  color: white;
  padding: 1rem 2rem;
  border-radius: 50px;
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.2);
  font-weight: 600;
  animation: slideUp 0.3s ease;
}

@keyframes slideUp {
  from {
    transform: translate(-50%, 100px);
    opacity: 0;
  }
  to {
    transform: translate(-50%, 0);
    opacity: 1;
  }
}

.footer {
  background: #ea580c;
  color: #a8a29e;
  text-align: center;
  padding: 2rem;
  margin-top: 2rem;
}

@media (max-width: 768px) {
  .hero-content h1 {
    font-size: 2rem;
  }
  .tickets-grid {
    grid-template-columns: 1fr;
  }
}
</style>
