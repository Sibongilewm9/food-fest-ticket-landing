# food-fest-ticket-landing

## Project Overview
This is a single-page landing for Cape Town Food Fest 2026. Displays Bronze, Silver, and Gold ticket tiers with pricing and benefits. Users can favourite tiers to simulate engagement. The Silver tier is highlighted as "Most Popular" with distinct styling. Built as Module 1 Exercise 02 for Frontend Web Development.

This is a frontend prototype - no purchasing or backend integration yet. All data is local.

## Features
- **Dynamic Ticket Cards**: Rendered from local data using reusable Vue components
- **Featured Tier Highlight**: Silver tier uses scale, border, and badge to stand out
- **Favourite Interaction**: Click star icon to favourite/unfavourite. Counter shows in bottom bar
- **Responsive Layout**: Grid adapts from 3-col desktop to 1-col mobile
- **Slots**: Card action button uses `<slot>` for flexible content
- **Props & Events**: Parent passes ticket data via props, cards emit favourite events
- **CTA Button**: "Notify Me" button included as stretch goal

# Installation and run instructions
1.npm install
2.npm run dev
3.open http://localhost:5173

Screenshot of interface:
<img width="1881" height="875" alt="{DB2D2311-EB0E-4EB1-AD7B-723343D010C8}" src="https://github.com/user-attachments/assets/c1f1d84c-84a9-4f17-b0bb-8d5a99ebfcd1" />
