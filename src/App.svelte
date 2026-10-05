<script>
import heroImage from './vX2cDW8LUWk-HD.jpg';
const visited=[
['Roxie & Barry','Italian-led restaurant and bar with European plates, cocktails and a polished Whitefield setting.'],
['Tall Oaks','Nature-inspired, pet-friendly dining with lush open spaces and a resort-like feel.'],
['Tropika Brewing Co','Tropical-themed brewpub built around unhurried craft beer and an easygoing escape.'],
['Gladia Brewery & Kitchen','Roman-inspired brewery with grand interiors, in-house craft beer and global flavours.'],
['Mykos Craft Kitchen & Bar','Rooftop craft kitchen and bar mixing global cuisines, live entertainment and city views.'],
['Masterpiece Buffet','Large-format buffet spanning Indian, Mediterranean, biryani and Andhra favourites.'],
['Koko Samba','Lively Bengaluru dining stop with a bold, contemporary night-out atmosphere.']
].map(([name,description],i)=>({rank:i+1,name,description}));
const bucket=[
["Helen's Place — Marathahalli",'Neighbourhood restaurant and bar in Marathahalli with a relaxed, social setting.'],
['Beige Bangalore','Rooftop pub and lounge known for its stylish lighting, cocktails and live entertainment.'],
['Brix and Barrells','Mahadevapura brewpub with craft beer, live music and a casual group-friendly vibe.'],
['URU (Kaavu) — Whitefield','A green, design-forward dining concept built for laid-back food and drink sessions.'],
['Legends Microbrewery','Microbrewery destination centred on fresh beer, pub food and a lively evening atmosphere.'],
['The Azulian House','Design-led Bengaluru dining destination with an atmospheric, occasion-worthy setting.'],
['Nusa — Tropical Brewvilla','Balinese-inspired tropical brewscape with craft beer, global plates, live music and lush visuals.'],
["Helen & Lorena's Place",'Sarjapur Road brew-and-dine destination with a spacious setting for food, drinks and groups.'],
['The Estate Deli','Contemporary deli-style dining with a relaxed setting and an all-day, easygoing feel.'],
['The Porcupine — A Proper Indian Public House','Indian-first pub serving house beer, Indian spirits and freshly made homestyle food.'],
['HEYOU — MG Road','Two-level dining and bar spot pairing comfort food and cocktails with a livelier downstairs room.'],
['Baci Baci Osteria','Italian osteria from Frothy Tales focused on wood-fired cooking, pizza and long evenings.'],
["Molly's Courtyard",'Courtyard restaurant bringing together global plates, Korean specialties, pizzas and cocktails.'],
['Serious Slice — Cunningham Road','Light-filled pizzeria built around 72-hour sourdough, wood-fired pizza and fresh pasta.'],
["Cleo's Up Top",'Elevated Bengaluru hangout aimed at drinks, food and a rooftop-style night-out vibe.'],
['Candles Brewhouse','12th-floor Hebbal microbrewery pairing craft beer and global food with panoramic city views.'],
['The Clink','Bar-forward Bengaluru hangout designed around drinks, music and a social evening atmosphere.'],
['Mac Brew Farm','Electronic City brew-farm style spot serving beer alongside kebabs, biryani and open-air seating.'],
['Nido Craft Kitchen & Bar','Sahakara Nagar kitchen and bar with multicuisine plates, cocktails and indoor-outdoor seating.'],
['Sunrise Bar and Lounge','Large family garden bar and restaurant with terrace seating, draught beer and multicuisine food.'],
['Zero Degree On The Hill Brewery And Kitchen','RR Nagar brewery and kitchen serving pub favourites, Indian plates, cocktails and beer.'],
['Suka Brew and Kitchen','Nagarbhavi rooftop and waterfront-style lounge with a broad Indian and Asian-leaning menu.'],
['Paros — Brewery & Kitchen','Aegean-inspired rooftop brewery pairing small-batch beer, global food and sunset-friendly spaces.'],
['Oia Bangalore','Santorini-inspired mega-pub with dramatic architecture, open-air spaces, beer and live entertainment.']
].map(([name,description])=>({name,description})).sort((a,b)=>a.name.localeCompare(b.name, 'en', {sensitivity:'base'}));
const cover=[{name:'Pangeo',description:'High-end Brigade Road lounge blending global dining, cocktails and high-energy nightlife.',note:'Cover charge requested for a solo visit despite the listing showing free entry.'}];
let active='visited';
const tabs=[['visited','Visited',visited.length],['bucket','Bucket list',bucket.length],['cover','Need cover charge',cover.length]];
</script>
<svelte:head><title>Blore Lore — Bengaluru trail</title></svelte:head>
<div class="top-banner"><span>Tawan</span><a href="mailto:tawanjsingh@gmail.com">tawanjsingh@gmail.com</a></div>
<div class="shell">
<header><div class="eyebrow">BENGALURU · PERSONAL INDEX</div><h1>Blore <span>Lore.</span></h1><p class="intro">Places worth remembering, places still calling, and places that made entry complicated.</p><div class="stats"><div><strong>{visited.length}</strong><span>visited</span></div><div><strong>{bucket.length}</strong><span>to go</span></div><div><strong>{cover.length}</strong><span>caution</span></div></div></header>
<nav>{#each tabs as t}<button class:active={active===t[0]} onclick={()=>active=t[0]}><span>{t[1]}</span><small>{t[2]}</small></button>{/each}</nav>
<main>
{#if active==='visited'}<div class="section-head"><div><span class="kicker">VISITED</span><h2>Been there.</h2></div><p>Tawan's picks, in order.</p></div><div class="rank-list">{#each visited as p}<article class:podium={p.rank<=3}><div class="rank">#{p.rank}</div><div class="place"><h3>{p.name}</h3><span>{p.description}</span></div>{#if p.rank===1}<div class="badge">TOP PICK</div>{/if}</article>{/each}</div>
{:else if active==='bucket'}<div class="section-head"><div><span class="kicker">NEXT UP</span><h2>Still on the list.</h2></div><p>Places Tawan hasn't visited yet.</p></div><div class="cards">{#each bucket as p,i}<article class="card"><span class="index">{String(i+1).padStart(2,'0')}</span><div><h4>{p.name}</h4><p>{p.description}</p></div><span class="arrow">↗</span></article>{/each}</div>
{:else}<div class="section-head"><div><span class="kicker">THE FINE PRINT</span><h2>Need cover charge.</h2></div><p>Places separated out when entry comes with an extra condition.</p></div><div class="cover-grid">{#each cover as p}<article class="cover-card"><div class="warning">₹</div><div><h3>{p.name}</h3><p>{p.description}</p><p class="cover-note">{p.note}</p></div></article>{/each}</div>{/if}
</main><footer><span>BLR / 2026</span><span>EAT · SHOOT · RANK · REPEAT</span></footer></div>