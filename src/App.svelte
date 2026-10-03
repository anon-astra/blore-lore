<script>
const visited=[['Roxie & Barry'],['Tall Oaks','12 km'],['Tropika'],['Gladia','12 km'],['Mykos'],['Masterpiece'],['Koko Samba']].map((x,i)=>({rank:i+1,name:x[0],distance:x[1]}));
const bucket=[
["Helen's Place Marathahalli",'Under 10 km'],['Beige Bangalore','Under 10 km'],['Brix and Barrells','Under 10 km'],['URU (Kaavu) - Whitefield','Under 10 km'],
['Legends Microbrewery','10–20 km'],['The Azulian House','10–20 km'],['Nusa - Tropical Brewvilla','10–20 km'],["Helen & Lorena's Place",'10–20 km','13 km'],['The Estate Deli','10–20 km'],['The Porcupine','10–20 km'],['Heyou','10–20 km'],['Baci Baci Osteria','10–20 km'],["Molly's Courtyard",'10–20 km'],['Serious Slice - Cunningham Road','10–20 km'],
["Cleo's Up Top",'20+ km'],['Candles Brewhouse','20+ km'],['The Clink','20+ km'],['MAC Brew Farm','20+ km'],['Nido - Craft Kitchen & Bar','20+ km'],['Sunrise Bar and Lounge','20+ km'],['Zero Degree On The Hill Brewery And Kitchen','20+ km'],['SUKA - Brew and Kitchen','20+ km'],['Paros - Brewery & Kitchen','20+ km']
].map(x=>({name:x[0],zone:x[1],distance:x[2]}));
const cover=[{name:'Pangeo',note:'Cover charge requested for a solo visit despite the Dineout listing showing free entry.'}];
const zones=['Under 10 km','10–20 km','20+ km']; let active='visited';
const tabs=[['visited','Visited',visited.length],['bucket','Bucket list',bucket.length],['cover','Need cover charge',cover.length]];
</script>
<svelte:head><title>Blore Lore — Bengaluru trail</title></svelte:head>
<div class="shell">
<header><div class="eyebrow">BENGALURU · PERSONAL INDEX</div><h1>Blore<br><span>Lore.</span></h1><p class="intro">Places worth remembering, places still calling, and places that made entry complicated.</p><div class="stats"><div><strong>{visited.length}</strong><span>visited</span></div><div><strong>{bucket.length}</strong><span>to go</span></div><div><strong>{cover.length}</strong><span>cover</span></div></div></header>
<nav>{#each tabs as t}<button class:active={active===t[0]} onclick={()=>active=t[0]}><span>{t[1]}</span><small>{t[2]}</small></button>{/each}</nav>
<main>
{#if active==='visited'}<div class="section-head"><div><span class="kicker">THE RANKING</span><h2>Been there.</h2></div><p>Your personal ranking, pulled from the Ranking sheet.</p></div><div class="rank-list">{#each visited as p}<article class:podium={p.rank<=3}><div class="rank">#{p.rank}</div><div class="place"><h3>{p.name}</h3>{#if p.distance}<span>{p.distance} away</span>{/if}</div>{#if p.rank===1}<div class="badge">TOP PICK</div>{/if}</article>{/each}</div><p class="source-note">Ranking snapshot · 03 Oct 2026</p>
{:else if active==='bucket'}<div class="section-head"><div><span class="kicker">NEXT UP</span><h2>Still on the list.</h2></div><p>Grouped by driving distance from AECS Layout.</p></div>{#each zones as z}<section class="zone"><div class="zone-title"><h3>{z}</h3><span>{bucket.filter(p=>p.zone===z).length}</span></div><div class="cards">{#each bucket.filter(p=>p.zone===z) as p,i}<article class="card"><span class="index">{String(i+1).padStart(2,'0')}</span><div><h4>{p.name}</h4>{#if p.distance}<p>{p.distance} driving</p>{/if}</div><span class="arrow">↗</span></article>{/each}</div></section>{/each}
{:else}<div class="section-head"><div><span class="kicker">THE FINE PRINT</span><h2>Need cover charge.</h2></div><p>Places separated out when entry comes with an extra condition.</p></div><div class="cover-grid">{#each cover as p}<article class="cover-card"><div class="warning">₹</div><div><h3>{p.name}</h3><p>{p.note}</p></div></article>{/each}</div>{/if}
</main><footer><span>BLR / 2026</span><span>EAT · SHOOT · RANK · REPEAT</span></footer></div>