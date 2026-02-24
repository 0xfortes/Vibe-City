# VibeCITY — Product Description & Build Notes

## One-Liner
**VibeCITY is a living city personality engine where AI agents debate what you should do tonight — not a chatbot, not a search tool, but a spectator sport for city discovery.**

---

## The Problem
Every city discovery app is the same: search bar → list of results → reviews. It's Google Maps with lipstick. TripAdvisor with AI. Nobody opens these apps for fun. Nobody shares a list of restaurants.

## The Insight
People don't want *information* about cities — they want to *feel* the city before they arrive. They want opinions, contradictions, hot takes, and the insider knowledge that makes a trip legendary. They want what they'd get if they had 5 opinionated local friends arguing about where to take them.

## The Concept: The Council
VibeCITY drops 5 AI agents into every city. Each has a distinct personality, perspective, and domain:

| Agent | Name | Domain | Personality |
|-------|------|--------|-------------|
| 🦉 | The Nightowl | Nightlife & After Dark | Bold, opinionated, knows every door policy and secret party |
| 🍜 | The Foodie | Food & Drink | Passionate, specific, will fight over taco rankings |
| 🎭 | The Culture Vulture | Art, Music, Events | Cerebral, taste-maker, always knows what's opening |
| 🏮 | The Local Legend | Insider Knowledge | Been there 10 years, knows what tourists never find |
| 🧭 | The Wanderer | Exploration & Serendipity | Anti-plan, pro-getting-lost, believes the city reveals itself |

**These agents don't just answer questions — they debate each other in real-time.** They disagree. They tag each other. They have hot takes. You watch the debate unfold like a group chat, then steer it by asking follow-up questions.

---

## What Makes It Go Viral

### 1. Vibe Scores (The Shareable Hook)
Every city gets a real-time **Vibe Score** (0-100) with sub-scores for Nightlife, Food, Culture, Locals, and Wander. These update based on events, weather, social signals, and time of day. Users share their city's Vibe Card on Instagram/TikTok like a personality test result. "Berlin is 87 tonight 🔥" becomes a meme format.

### 2. The Council is Entertainment
Unlike chatbots where you type and wait, The Council is a *spectator experience*. Messages appear one by one, agents reference and disagree with each other, and you're watching a live debate. It's closer to a podcast or a group chat than a search engine. People will screenshot these debates and share them.

### 3. Hot Takes > Neutral Info
Every agent has a personality. The Nightowl will trash tourist traps. The Foodie will start wars over which taco stand is best. The Local will gatekeep. This creates emotional reactions — agreement, disagreement, sharing, arguing in comments. Neutral information doesn't go viral. Opinions do.

### 4. "Your Turn" Mechanic
After the agents debate, you get prompted with follow-up questions to steer the conversation. "Tell me more about that parking garage party" or "What would a local NEVER do?" This creates engagement loops and makes every session unique.

### 5. Vibe Alerts
Push notifications when a city's vibe spikes: "Tokyo's nightlife score just hit 98 — cherry blossom parties are erupting across Shibuya 🌸" These are shareable, timely, and create FOMO.

---

## Key Screens (MVP)

### Home Screen
- Search bar with "Drop a city..."
- Trending cities with live Vibe Scores
- Scrollable Vibe Cards for top cities

### City View
- City name + generated tagline (e.g., "Chaos with impeccable taste")
- Vibe Score card with animated sub-score bars
- Share Vibe Card button
- The Council debate (live-appearing messages)
- "Your Turn" follow-up prompts

### Future Screens
- **Spots Map**: All mentioned places pinned on a map, filterable by agent
- **Stories**: Short-form content from real locals verifying/disputing agent claims
- **My Plan**: Save recommendations into a shareable itinerary
- **Vibe Map**: Global map showing real-time vibe scores of every city

---

## Technical Architecture

### Backend
- **Multi-Agent Orchestration**: Each agent is a separate prompt/persona with its own system prompt, personality, and knowledge context. Use a coordinator agent that decides speaking order and manages the debate flow.
- **Real-Time Vibe Score Engine**: Aggregate signals from event APIs (Eventbrite, Dice, RA), weather APIs, time of day, social sentiment (X/Reddit), and local calendar data to compute live Vibe Scores per city.
- **City Knowledge Base**: RAG system per city with curated local knowledge, venue data, event calendars, and neighborhood guides.
- **Streaming Responses**: Each agent message streams in real-time with typing indicators for the "live debate" feel.

### Frontend
- React Native (mobile-first) or Next.js (web)
- Framer Motion for the staggered message animations
- WebSocket for real-time Council debates
- Share API for native Vibe Card sharing (generate OG images server-side)

### AI Stack
- Claude API for agent personalities (separate system prompts per agent)
- Web search tool for real-time local events and venue info
- Structured outputs for extracting venues, addresses, and map pins from agent responses
- Function calling for agents to reference each other and react

### Data Sources
- Google Places API (venues, ratings, hours)
- Event APIs (Eventbrite, Resident Advisor, Dice, local calendars)
- Weather API (OpenWeather)
- Social signals (Reddit, X API for sentiment)
- User-generated tips and corrections

---

## Monetization Ideas
- **Free tier**: 3 Council debates per day, Vibe Scores always free
- **VibeCITY Pro**: Unlimited debates, save plans, Vibe Alerts, agent customization
- **City Partnerships**: Tourism boards sponsor featured city content
- **Affiliate**: Booking links for restaurants, experiences (disclose transparently)
- **Vibe Reports**: B2B — sell city vibe analytics to hospitality, real estate, tourism

---

## What This Is NOT
- ❌ Not a chatbot (you don't type open-ended prompts)
- ❌ Not a GPT wrapper (agents have persistent personalities, debate each other, and use real-time data)
- ❌ Not a review aggregator (opinions, not star ratings)
- ❌ Not a travel planner (it's a vibe check first, planning second)

## What This IS
- ✅ Entertainment + utility (you open it for fun, leave with a plan)
- ✅ A personality engine for cities
- ✅ A shareable, social-first experience
- ✅ The answer to "should I go there?" before you even search for flights

---

## V1 MVP Scope
1. Home screen with city search + trending chips
2. City view with Vibe Score + animated bars
3. The Council debate (5 agents, pre-orchestrated flow, real-time streaming feel)
4. "Your Turn" follow-ups that trigger new agent rounds
5. Share Vibe Card (generate image for social)
6. 10 launch cities: Tokyo, Berlin, Mexico City, Lisbon, NYC, Paris, London, Bangkok, Buenos Aires, Istanbul

## V2 Features
- Spots Map with all recommended venues
- User reactions on agent messages (upvote/downvote)
- Custom agent personas (add your own agent type)
- Local Stories (user-submitted short clips)
- Vibe Alerts (push notifications)
- Trip Plan builder

---

*Built for the people who ask locals, not Google.*
