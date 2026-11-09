'use strict';
// ConquiMina - servidor sin dependencias.  Uso: node server.js   (PORT y OWNER_KEY opcionales)
const http = require('http'), fs = require('fs'), path = require('path'), crypto = require('crypto');
const PORT = +process.env.PORT || 3000, FILE = path.join(__dirname, 'data.json');
const now = () => Date.now(), clamp = (v, a, b) => Math.min(b, Math.max(a, v));

/* ---------- DATOS DEL JUEGO ---------- */
const MINERALS = [
  { id: 'carbon', name: 'Carbón', emoji: '⚫', p: 40, value: 2, prestige: 0, rarity: 'comun' },
  { id: 'hierro', name: 'Hierro', emoji: '🔩', p: 25, value: 4, prestige: 0, rarity: 'comun' },
  { id: 'cobre', name: 'Cobre', emoji: '🟠', p: 15, value: 10, prestige: 1, rarity: 'comun' },
  { id: 'oro', name: 'Oro', emoji: '🥇', p: 8, value: 60, prestige: 5, rarity: 'raro' },
  { id: 'litio', name: 'Litio', emoji: '🔋', p: 5, value: 100, prestige: 10, rarity: 'raro' },
  { id: 'diamante', name: 'Diamante', emoji: '💎', p: 3, value: 400, prestige: 40, rarity: 'epico' },
  { id: 'platino', name: 'Platino', emoji: '⚪', p: 2, value: 800, prestige: 100, rarity: 'epico' },
  { id: 'uranio', name: 'Uranio', emoji: '☢️', p: 1, value: 1500, prestige: 300, rarity: 'legendario' },
  { id: 'esmeralda', name: 'Esmeralda', emoji: '🟢', p: 1, value: 2000, prestige: 500, rarity: 'legendario' },
];
const COUNTRIES = [
  ['cl', 'Chile', '🇨🇱', 'Cobre', '🔶', 2.4, 60], ['ar', 'Argentina', '🇦🇷', 'Litio', '🔋', 2.2, 70],
  ['br', 'Brasil', '🇧🇷', 'Café', '☕', 2.6, 140], ['pe', 'Perú', '🇵🇪', 'Plata', '🥈', 2.0, 55],
  ['co', 'Colombia', '🇨🇴', 'Petróleo', '🛢️', 2.2, 65], ['mx', 'México', '🇲🇽', 'Aguacate', '🥑', 2.3, 110],
  ['ve', 'Venezuela', '🇻🇪', 'Petróleo', '🛢️', 2.5, 80], ['bo', 'Bolivia', '🇧🇴', 'Gas natural', '🔥', 1.8, 40],
  ['ec', 'Ecuador', '🇪🇨', 'Banano', '🍌', 1.7, 45], ['uy', 'Uruguay', '🇺🇾', 'Carne', '🥩', 1.6, 35],
  ['py', 'Paraguay', '🇵🇾', 'Energía', '⚡', 1.6, 38], ['cu', 'Cuba', '🇨🇺', 'Azúcar', '🍬', 1.5, 50],
  ['us', 'Estados Unidos', '🇺🇸', 'Maíz', '🌽', 4.5, 420], ['ca', 'Canadá', '🇨🇦', 'Madera', '🪵', 3.2, 220],
  ['sa', 'Arabia Saudita', '🇸🇦', 'Petróleo', '🛢️', 4.2, 260], ['ru', 'Rusia', '🇷🇺', 'Gas natural', '🔥', 4.0, 380],
  ['cn', 'China', '🇨🇳', 'Tierras raras', '🧲', 4.8, 450], ['in', 'India', '🇮🇳', 'Té', '🍵', 3.0, 300],
  ['jp', 'Japón', '🇯🇵', 'Autos', '🚗', 3.8, 280], ['de', 'Alemania', '🇩🇪', 'Maquinaria', '⚙️', 3.6, 250],
  ['fr', 'Francia', '🇫🇷', 'Vino', '🍷', 3.1, 230], ['es', 'España', '🇪🇸', 'Aceite de oliva', '🫒', 2.4, 150],
  ['it', 'Italia', '🇮🇹', 'Pasta', '🍝', 2.6, 170], ['gb', 'Reino Unido', '🇬🇧', 'Lana', '🐑', 2.9, 240],
  ['au', 'Australia', '🇦🇺', 'Hierro', '⛏️', 3.3, 200], ['za', 'Sudáfrica', '🇿🇦', 'Platino', '⚪', 2.5, 120],
  ['ng', 'Nigeria', '🇳🇬', 'Petróleo', '🛢️', 2.1, 100], ['eg', 'Egipto', '🇪🇬', 'Algodón', '☁️', 1.9, 90],
  ['tr', 'Turquía', '🇹🇷', 'Avellanas', '🌰', 2.2, 160], ['id', 'Indonesia', '🇮🇩', 'Aceite de palma', '🌴', 2.4, 150],
  ['th', 'Tailandia', '🇹🇭', 'Arroz', '🍚', 2.0, 95], ['kr', 'Corea del Sur', '🇰🇷', 'Chips', '💾', 3.4, 260],
  ['no', 'Noruega', '🇳🇴', 'Salmón', '🐟', 2.3, 85], ['ch', 'Suiza', '🇨🇭', 'Chocolate', '🍫', 2.7, 75],
  ['cd', 'R.D. Congo', '🇨🇩', 'Cobalto', '🔵', 1.9, 70], ['nz', 'Nueva Zelanda', '🇳🇿', 'Leche', '🥛', 1.8, 60],
  ['ma', 'Marruecos', '🇲🇦', 'Fosfato', '🧪', 1.7, 65], ['ke', 'Kenia', '🇰🇪', 'Flores', '🌹', 1.5, 45],
].map(([id, name, flag, res, emoji, rate, def]) => ({ id, name, flag, res, emoji, rate, def }));
const CFG = {
  mine: { n: 'Minas', e: '⛏️', base: 40, g: 1.55, max: 80, d: '+1 minero por nivel' },
  city: { n: 'Ciudades', e: '🏙️', base: 120, g: 1.6, max: 60, d: '+20% ingresos pasivos' },
  security: { n: 'Seguridad', e: '🚔', base: 100, g: 1.55, max: 25, d: '-3% delincuencia' },
  military: { n: 'Militar', e: '🪖', base: 150, g: 1.6, max: 80, d: '+poder de conquista' },
  quality: { n: 'Calidad de vida', e: '😊', base: 130, g: 1.58, max: 60, d: '+3% ingresos y +5% ventas' },
  tech: { n: 'Tecnología', e: '🧪', base: 200, g: 1.7, max: 30, d: 'Minas más rápidas, +ventas, +poder' },
};
const WHEEL = [2, 3, 5, 10, 20, 50];
const EV_W = [[2, 40], [3, 25], [5, 15], [10, 10], [20, 6], [50, 4]];

/* ---------- ESTADO ---------- */
let S = { players: {}, sessions: {}, registry: [], chat: [], offers: [], event: null, evh: [], market: {}, secret: [], seq: {}, ownerKey: '', nextAuto: 0 };
try { Object.assign(S, JSON.parse(fs.readFileSync(FILE, 'utf8'))); } catch (e) { }
S.seq = Object.assign({ reg: 0, chat: 0, offer: 0, ev: 0, sec: 0 }, S.seq);
if (process.env.OWNER_KEY) S.ownerKey = process.env.OWNER_KEY;
if (!S.ownerKey) S.ownerKey = crypto.randomBytes(5).toString('hex');
if (!S.nextAuto) S.nextAuto = now() + 180000;
for (const k in S.players) { const p = S.players[k]; p.notes = p.notes || []; p.inv = p.inv || {}; }
let dirty = true;
setInterval(() => { if (!dirty) return; dirty = false; try { fs.writeFileSync(FILE + '.tmp', JSON.stringify(S)); fs.renameSync(FILE + '.tmp', FILE); } catch (e) { console.error(e); } }, 4000);

/* ---------- UTILIDADES ---------- */
function wpick(list) { let r = Math.random() * list.reduce((a, x) => a + x[1], 0); for (const [v, w] of list) { if ((r -= w) < 0) return v; } return list[0][0]; }
const roll = () => wpick(MINERALS.map(m => [m, m.p]));
const defs = () => MINERALS.concat(S.secret.map(s => ({ id: s.id, name: s.name, emoji: s.emoji, value: s.value, prestige: Math.max(1, Math.round(s.value / 10)), rarity: 'secreto', p: 0 })));
const getDef = id => defs().find(d => d.id === id);
const country = id => COUNTRIES.find(c => c.id === id);
const fmt = n => { n = Math.floor(n); const u = ['', 'K', 'M', 'B', 'T', 'Qa', 'Qi']; let i = 0, x = n; while (x >= 1000 && i < u.length - 1) { x /= 1000; i++; } return (i ? x.toFixed(x < 10 ? 2 : x < 100 ? 1 : 0) : x) + u[i]; };
const needXp = l => Math.floor(40 * Math.pow(l, 1.5));

const crime = p => clamp(30 + 4 * (p.countries.length - 1) - 3 * p.up.security, 0, 85);
const incomeMult = p => (1 + 0.2 * p.up.city) * (1 - crime(p) / 150) * (1 + 0.03 * p.up.quality);
const passive = p => p.countries.reduce((a, id) => a + (country(id) ? country(id).rate : 0), 0) * incomeMult(p);
const power = p => (1 + p.up.military) * 8 * (1 + 0.08 * p.up.tech);
const cooldown = p => Math.max(500, 1800 - p.up.tech * 60);
const miners = p => 2 + p.up.mine;
const sellMult = p => 1 + 0.05 * p.up.quality + 0.03 * p.up.tech;
const empire = p => Math.floor(p.countries.length * 500 + p.up.military * 25 + p.up.city * 15 + p.up.tech * 15 + p.up.quality * 8 + p.up.security * 8 + p.up.mine * 10);
const title = p => { const n = p.countries.length; return n >= 20 ? 'Imperio Galáctico' : n >= 12 ? 'Imperio' : n >= 6 ? 'Gran Reino' : n >= 3 ? 'Reino' : n >= 2 ? 'Ciudad-Estado' : 'Aldea'; };
const convCost = (p, c) => Math.floor(c.def * 400 * (1 + 0.15 * (p.countries.length - 1)));
const convChance = (p, c) => clamp(power(p) / (power(p) + c.def * 1.5), 0.05, 0.95);
const upCost = (k, l) => Math.floor(CFG[k].base * Math.pow(CFG[k].g, l));

function newPlayer(name, pass, cid) {
  const salt = crypto.randomBytes(16).toString('hex');
  return { name, salt, hash: crypto.scryptSync(pass, salt, 32).toString('hex'), country: cid, countries: [cid], money: 60, prestige: 0, xp: 0, level: 1,
    up: { mine: 0, city: 0, security: 0, military: 0, quality: 0, tech: 0 }, inv: {}, found: 0, lastMine: 0, lastTick: now(), chest: 0, streak: 0, lastSeen: now(), created: now(), notes: [] };
}
function settle(p) {
  const t = now(); const dt = Math.min((t - p.lastTick) / 1000, 28800);
  if (dt > 0) {
    let extra = 0;
    for (const e of S.evh) { const ov = Math.min(t, e.endsAt) - Math.max(p.lastTick, e.startedAt); if (ov > 0) extra += ov / 1000 * (e.mult - 1); }
    p.money += passive(p) * (dt + extra);
  }
  p.lastTick = t; p.lastSeen = t;
}
function addXp(p, x) {
  p.xp += x;
  while (p.xp >= needXp(p.level)) { p.xp -= needXp(p.level); p.level++; const r = 100 * p.level; p.money += r; p.notes.push({ k: 'lvl', txt: `⭐ ¡Nivel ${p.level}! +$${fmt(r)}` }); }
}
function award(p, d, qty, gift) {
  p.inv[d.id] = (p.inv[d.id] || 0) + qty; p.found += qty;
  const pr = d.prestige * qty; p.prestige += pr;
  if (d.rarity !== 'comun') { S.registry.unshift({ id: ++S.seq.reg, t: now(), user: p.name, c: p.country, m: d.id, qty, pr, g: !!gift }); if (S.registry.length > 300) S.registry.length = 300; }
  return pr;
}
const evActive = () => (S.event && S.event.endsAt > now() ? S.event : null);
function startEvent(mult, dur, by) {
  const t = now(); if (S.event && S.event.endsAt > t) S.event.endsAt = t;
  const e = { id: ++S.seq.ev, mult, startedAt: t, endsAt: t + dur * 1000, by, wheel: [...new Set([...WHEEL, mult])].sort((a, b) => a - b) };
  S.event = e; S.evh.push(e); if (S.evh.length > 30) S.evh.shift(); dirty = true; return e;
}
function tickMarket() { for (const m of MINERALS) S.market[m.id] = +clamp((S.market[m.id] || 1) + (Math.random() - 0.5) * 0.35, 0.8, 1.9).toFixed(2); }
tickMarket(); setInterval(tickMarket, 45000);
setInterval(() => { if (!evActive() && now() > S.nextAuto) { startEvent(wpick(EV_W), 90, 'auto'); S.nextAuto = now() + (480 + Math.random() * 420) * 1000; } }, 5000);

/* ---------- VISTAS ---------- */
function view(p) {
  const owned = new Set(p.countries);
  return { name: p.name, country: p.country, countries: p.countries, money: p.money, prestige: p.prestige, level: p.level, xp: p.xp, need: needXp(p.level), found: p.found, streak: p.streak,
    up: Object.fromEntries(Object.keys(CFG).map(k => [k, { l: p.up[k], cost: p.up[k] >= CFG[k].max ? null : upCost(k, p.up[k]) }])),
    inv: Object.entries(p.inv).filter(e => e[1] > 0).map(([id, q]) => ({ id, q })),
    passive: passive(p), miners: miners(p), cd: cooldown(p), crime: crime(p), power: power(p), sell: sellMult(p), empire: empire(p), title: title(p),
    chestIn: Math.max(0, p.chest - now()),
    targets: COUNTRIES.filter(c => !owned.has(c.id)).map(c => ({ id: c.id, cost: convCost(p, c), chance: convChance(p, c) })) };
}
const ok = (p, o = {}) => Object.assign(o, { me: view(p), notes: p.notes.splice(0) });
const err = m => ({ err: m });
function offerView(o) {
  const d = getDef(o.m) || { value: 1 }; const bank = o.qty * d.value * 0.8, mk = o.qty * d.value * (S.market[o.m] || 1);
  return { id: o.id, seller: o.seller, m: o.m, qty: o.qty, price: o.price, sg: +((o.price / bank - 1) * 100).toFixed(1), bg: +((mk / o.price - 1) * 100).toFixed(1) };
}

/* ---------- TRADUCCIÓN DEL CHAT ---------- */
const tr = new Map(), pend = new Set();
async function translate(text, lang) {
  if (typeof fetch !== 'function') return null;
  try {
    const r = await fetch('https://translate.googleapis.com/translate_a/single?client=gtx&sl=auto&tl=' + lang + '&dt=t&q=' + encodeURIComponent(text), { signal: AbortSignal.timeout(4000) });
    const j = await r.json(); return { t: j[0].map(x => x[0]).join(''), s: String(j[2] || '').split('-')[0] };
  } catch (e) { }
  try {
    const r = await fetch('https://api.mymemory.translated.net/get?q=' + encodeURIComponent(text) + '&langpair=Autodetect|' + lang, { signal: AbortSignal.timeout(4000) });
    const j = await r.json(); const t = j.responseData && j.responseData.translatedText;
    if (t && !/MYMEMORY WARNING/i.test(t)) return { t, s: '?' };
  } catch (e) { }
  return null;
}
function askTr(m, lang) {
  const k = m.id + '|' + lang; if (pend.has(k)) return; pend.add(k);
  translate(m.x, lang).then(r => {
    tr.set(k, r && r.s !== lang && r.t.trim().toLowerCase() !== m.x.trim().toLowerCase() ? r : 0);
    pend.delete(k); if (tr.size > 6000) tr.delete(tr.keys().next().value);
  });
}
const chatView = lang => S.chat.slice(-40).map(m => {
  const o = { id: m.id, u: m.u, x: m.x, ts: m.ts }, c = tr.get(m.id + '|' + lang);
  if (c) o.t = c.t; else if (c === undefined) askTr(m, lang);
  return o;
});

/* ---------- RUTAS ---------- */
function sellOne(p, d, qty) {
  qty = Math.min(qty, p.inv[d.id] || 0); if (qty <= 0) return 0;
  p.inv[d.id] -= qty; if (!p.inv[d.id]) delete p.inv[d.id];
  const g = qty * d.value * 0.8 * sellMult(p); p.money += g; return g;
}
function targetsOf(t, me) {
  const all = Object.values(S.players); t = String(t || '').trim();
  if (!t) return [me]; if (t.toUpperCase() === 'ALL') return all;
  if (t.toUpperCase() === 'ONLINE') return all.filter(x => now() - x.lastSeen < 60000);
  const x = S.players[t.toLowerCase()]; return x ? [x] : [];
}
const routes = {
  'GET /api/static': { open: true, f: () => ({ minerals: MINERALS, countries: COUNTRIES, cfg: CFG }) },
  'POST /api/register': { open: true, f: ({ b }) => {
    const name = String(b.name || '').trim(), pass = String(b.pass || '');
    if (!/^[\p{L}\p{N}_ ]{3,16}$/u.test(name)) return err('Nombre: 3-16 letras o números');
    if (pass.length < 4) return err('Clave: mínimo 4 caracteres');
    if (!country(b.country)) return err('Elige un país');
    const key = name.toLowerCase(); if (S.players[key]) return err('Ese nombre ya existe');
    S.players[key] = newPlayer(name, pass, b.country);
    const token = crypto.randomBytes(24).toString('hex'); S.sessions[token] = key; dirty = true; return { token };
  } },
  'POST /api/login': { open: true, f: ({ b }) => {
    const p = S.players[String(b.name || '').trim().toLowerCase()]; if (!p) return err('Usuario o clave incorrectos');
    const h = crypto.scryptSync(String(b.pass || ''), p.salt, 32);
    if (!crypto.timingSafeEqual(h, Buffer.from(p.hash, 'hex'))) return err('Usuario o clave incorrectos');
    const token = crypto.randomBytes(24).toString('hex'); S.sessions[token] = p.name.toLowerCase(); dirty = true; return { token };
  } },
  'GET /api/poll': { f: ({ p, q }) => {
    let lang = q.get('lang') || 'es'; if (!/^[a-zA-Z]{2,3}(-[A-Za-z]{2,4})?$/.test(lang)) lang = 'es';
    const e = evActive();
    return ok(p, { now: now(), event: e, market: S.market, secrets: S.secret.map(s => getDef(s.id)),
      offers: S.offers.slice(-80).reverse().map(offerView), reg: S.registry.slice(0, 40),
      chat: chatView(lang), online: Object.values(S.players).filter(x => now() - x.lastSeen < 30000).length });
  } },
  'POST /api/mine': { f: ({ p }) => {
    const t = now(); if (t - p.lastMine < cooldown(p) * 0.85) return err('Los mineros están descansando...');
    p.streak = t - p.lastMine < 4000 ? p.streak + 1 : 1; p.lastMine = t;
    const e = evActive(), em = e ? e.mult : 1, counts = {};
    for (let i = 0; i < miners(p); i++) { const m = roll(); counts[m.id] = (counts[m.id] || 0) + em; }
    const drops = []; let best = null, gainPr = 0;
    for (const id in counts) { const d = getDef(id); gainPr += award(p, d, counts[id]); drops.push({ id, q: counts[id] }); if (!best || d.value > best.value) best = d; }
    const bonus = Math.floor(Math.min(p.streak, 50) * 1.5 * (1 + p.up.mine * 0.2) * em); p.money += bonus;
    addXp(p, Math.ceil(miners(p) * em * 0.8));
    return ok(p, { drops, best: best.id, bonus, streak: p.streak, pr: gainPr, em });
  } },
  'POST /api/sell': { f: ({ b, p }) => {
    let g = 0;
    if (b.all) { for (const id of Object.keys(p.inv)) { const d = getDef(id); if (d && d.rarity !== 'legendario' && d.rarity !== 'secreto') g += sellOne(p, d, p.inv[id]); } }
    else { const d = getDef(b.id); if (!d) return err('?'); g = sellOne(p, d, b.qty ? Math.floor(+b.qty) : p.inv[d.id] || 0); }
    if (g <= 0) return err('Nada que vender'); addXp(p, 1); return ok(p, { gain: g });
  } },
  'POST /api/upgrade': { f: ({ b, p }) => {
    const k = b.k; if (!CFG[k]) return err('?'); const l = p.up[k]; if (l >= CFG[k].max) return err('Nivel máximo');
    const c = upCost(k, l); if (p.money < c) return err('Te falta dinero'); p.money -= c; p.up[k]++; addXp(p, 4 + l);
    return ok(p, { k });
  } },
  'POST /api/conquer': { f: ({ b, p }) => {
    const c = country(b.id); if (!c) return err('?'); if (p.countries.includes(c.id)) return err('Ya es tuyo');
    const cost = convCost(p, c); if (p.money < cost) return err('Te falta dinero'); p.money -= cost;
    if (Math.random() < convChance(p, c)) { p.countries.push(c.id); const pr = Math.floor(25 + c.def / 5); p.prestige += pr; addXp(p, 20 + Math.floor(c.def / 4)); return ok(p, { win: true, c: c.id, pr }); }
    p.money += cost * 0.5; return ok(p, { win: false, c: c.id });
  } },
  'POST /api/chest': { f: ({ p }) => {
    if (now() < p.chest) return err('Aún no está listo'); p.chest = now() + 300000;
    const lv = Object.values(p.up).reduce((a, x) => a + x, 0), money = Math.floor((80 + 30 * lv) * (0.5 + Math.random() * 1.5)); p.money += money;
    let m = null; if (Math.random() < 0.3) { const d = roll(), q = 1 + Math.floor(Math.random() * 3); award(p, d, q); m = { id: d.id, q }; }
    addXp(p, 5); return ok(p, { money, m });
  } },
  'POST /api/trade/list': { f: ({ b, p }) => {
    const d = getDef(b.m); if (!d) return err('?'); const q = Math.floor(+b.qty), price = Math.floor(+b.price);
    if (!(q > 0) || !(price > 0) || price > 1e15) return err('Cantidad o precio inválido'); if ((p.inv[d.id] || 0) < q) return err('No tienes tantos');
    if (S.offers.filter(o => o.seller === p.name).length >= 10) return err('Máximo 10 ofertas');
    p.inv[d.id] -= q; if (!p.inv[d.id]) delete p.inv[d.id];
    S.offers.push({ id: ++S.seq.offer, seller: p.name, m: d.id, qty: q, price, t: now() }); return ok(p);
  } },
  'POST /api/trade/buy': { f: ({ b, p }) => {
    const i = S.offers.findIndex(o => o.id === +b.id); if (i < 0) return err('Oferta ya no disponible'); const o = S.offers[i];
    if (o.seller === p.name) return err('Es tu oferta'); if (p.money < o.price) return err('Te falta dinero');
    const s = S.players[o.seller.toLowerCase()], d = getDef(o.m); S.offers.splice(i, 1);
    p.money -= o.price; p.inv[o.m] = (p.inv[o.m] || 0) + o.qty;
    if (s) { s.money += o.price; s.notes.push({ k: 'sale', txt: `💰 ${p.name} te compró ${o.qty}× ${d.emoji} por $${fmt(o.price)}` }); }
    addXp(p, 3); return ok(p, { bought: offerView(o) });
  } },
  'POST /api/trade/cancel': { f: ({ b, p }) => {
    const i = S.offers.findIndex(o => o.id === +b.id && o.seller === p.name); if (i < 0) return err('?');
    const o = S.offers.splice(i, 1)[0]; p.inv[o.m] = (p.inv[o.m] || 0) + o.qty; return ok(p);
  } },
  'POST /api/chat': { f: ({ b, p }) => {
    const x = String(b.text || '').trim().slice(0, 200); if (!x) return err('?');
    if (now() - (p.lastChat || 0) < 1200) return err('Más despacio 🙂'); p.lastChat = now();
    S.chat.push({ id: ++S.seq.chat, u: p.name, x, ts: now() }); if (S.chat.length > 200) S.chat.shift(); return { ok: true };
  } },
  'GET /api/ranking': { f: ({ q, p }) => {
    const by = q.get('by'), key = { imperio: 'empire', dinero: 'money', minerales: 'found', prestigio: 'prestige' }[by] || 'empire';
    const all = Object.values(S.players).map(x => ({ name: x.name, flag: country(x.country).flag, title: title(x), countries: x.countries.length, empire: empire(x), money: Math.floor(x.money), found: x.found, prestige: x.prestige }));
    all.sort((a, b) => b[key] - a[key]); return { list: all.slice(0, 50), rank: all.findIndex(x => x.name === p.name) + 1, total: all.length, key };
  } },
  'POST /api/owner': { f: ({ b, p }) => {
    if (b.key !== S.ownerKey) return err('Clave del dueño incorrecta');
    const a = b.action;
    if (a === 'event') {
      const mult = b.mult ? clamp(Math.floor(+b.mult), 2, 50) : wpick(EV_W), dur = clamp(Math.floor(+b.dur) || 120, 10, 3600);
      startEvent(mult, dur, 'dueño'); return { ok: true, msg: `Evento x${mult} por ${dur}s` };
    }
    if (a === 'stop') { if (S.event) S.event.endsAt = now(); return { ok: true, msg: 'Evento detenido' }; }
    if (a === 'spawn') {
      const T = targetsOf(b.target, p); if (!T.length) return err('Sin destinatarios'); const n = clamp(Math.floor(+b.count) || 1, 1, 100000);
      for (const t of T) {
        if (b.kind === 'best') { const d = defs().sort((x, y) => y.value - x.value)[0]; award(t, d, n, true); t.notes.push({ k: 'gift'
