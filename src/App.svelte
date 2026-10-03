<script>
const visited=['Roxie & Barry','Tall Oaks','Tropika','Gladia','Mykos','Masterpiece','Koko Samba'].map((name,i)=>({rank:i+1,name}));
const bucket=["Helen's Place Marathahalli",'Beige Bangalore','Brix and Barrells','URU (Kaavu) - Whitefield','Legends Microbrewery','The Azulian House','Nusa - Tropical Brewvilla',"Helen & Lorena's Place",'The Estate Deli','The Porcupine','Heyou','Baci Baci Osteria',"Molly's Courtyard",'Serious Slice - Cunningham Road',"Cleo's Up Top",'Candles Brewhouse','The Clink','MAC Brew Farm','Nido - Craft Kitchen & Bar','Sunrise Bar and Lounge','Zero Degree On The Hill Brewery And Kitchen','SUKA - Brew and Kitchen','Paros - Brewery & Kitchen','Oia Bangalore'].map(name=>({name}));
const cover=[{name:'Pangeo',note:'Cover charge requested for a solo visit despite the Dineout listing showing free entry.'}];
let active='visited';
const tabs=[['visited','Visited',visited.length],['bucket','Bucket list',bucket.length],['cover','Need cover charge',cover.length]];
</script>
<svelte:head><title>Blore Lore — Bengaluru trail</title></svelte:head>
<div class="shell">
<header><div class="eyebrow">BENGALURU · PERSONAL INDEX</div><h1>Blore<br><span>Lore.</span></h1><p class="intro">Places worth remembering, places still calling, and places that made entry complicated.</p><div class="stats"><div><strong>{visited.length}</strong><span>visited</span></div><div><strong>{bucket.length}</strong><span>to go</span></div><div><strong>{cover.length}</strong><span>caution</span></div></div></header>
<nav>{#each tabs as t}<button class:active={active===t[0]} onclick={()=>active=t[0]}><span>{t[1]}</span><small>{t[2]}</small></button>{/each}</nav>
<main>
{#if active==='visited'}<div class="section-head"><div><span class="kicker">VISITED</span><h2>Been there.</h2></div><p>Tawan's picks, in order.</p></div><div class="rank-list">{#each visited as p}<article class:podium={p.rank<=3}><div class="rank">#{p.rank}</div><div class="place"><h3>{p.name}</h3></div>{#if p.rank===1}<div class="badge">TOP PICK</div>{/if}</article>{/each}</div>
{:else if active==='bucket'}<div class="section-head"><div><span class="kicker">NEXT UP</span><h2>Still on the list.</h2></div><p>Places Tawan hasn't visited yet.</p></div><div class="cards">{#each bucket as p,i}<article class="card"><span class="index">{String(i+1).padStart(2,'0')}</span><div><h4>{p.name}</h4></div><span class="arrow">↗</span></article>{/each}</div>
{:else}<div class="section-head"><div><span class="kicker">THE FINE PRINT</span><h2>Need cover charge.</h2></div><p>Places separated out when entry comes with an extra condition.</p></div><div class="cover-grid">{#each cover as p}<article class="cover-card"><div class="warning">₹</div><div><h3>{p.name}</h3><p>{p.note}</p></div></article>{/each}</div>{/if}
</main><footer><span>BLR / 2026</span><span>EAT · SHOOT · RANK · REPEAT</span></footer></div>