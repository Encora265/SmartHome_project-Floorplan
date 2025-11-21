# SmartHome_project Floorplan
# <span style="color:#3498db">🏡 Floorplan per Home Assistant</span>

Questo progetto contiene il mio floorplan personalizzato per Home Assistant: un'interfaccia grafica avanzata basata su immagini, overlay dinamici e controlli interattivi.
Il tutto è realizzato **in YAML**, senza moduli esterni complessi, ed è progettato per funzionare in modo fluido su tablet, dashboard wall e dispositivi touch.

L'obiettivo è creare un controllo immediato e intuitivo dell'intera casa: luci, sensori, media player, clima, consumi, porte/finestre, automazioni e molto altro.

---

## 🎥 Dimostrazione
<h2 id="panoramica-floorplan">📹 Dimostrazione</h2>

[![demo](www/repo/demo.gif)](https://www.youtube.com/watch?v=25UP5QQ9EAA&t=355s)

> ⚠️ Nota: alcune funzionalità mostrate nel video potrebbero differire leggermente dalla versione attuale del repository.

---

## 🖼️ Panoramica del Floorplan
<h2 id="dimostrazione">📹 Dimostrazione</h2>

Interfaccia progettata per dashboard moderne con una forte attenzione alla leggibilità e alla resa estetica.

<div align="center">
  <img src="/www/floorplan/main/main_day.png" width="49%" alt="Piano Terra - Notte">
  <img src="/www/floorplan/main/main_night.png" width="49%" alt="Primo Piano - Giorno">
</div>
<div align="center">
  <img src="/www/floorplan/terra/p0_night.png" width="49%" alt="Piano Terra - Notte">
  <img src="/www/floorplan/terrax/p0x_night.png" width="49%" alt="Primo Piano - Giorno">
</div>
<div align="center">
  <img src="/www/floorplan/primo/p1_night.png" width="49%" alt="Piano Terra - Notte">
  <img src="/www/floorplan/mansarda/mansarda_nigth.png" width="49%" alt="Primo Piano - Giorno">
</div>

<details>
<summary><strong>🌳 Struttura del Repository (Navigazione Rapida)</strong></summary>

<br>

**Clicca su qualsiasi voce per navigare direttamente alla sezione corrispondente:**

<pre>
SmartHome_project Floorplan
│
├── <a href="#dimostrazione">📹 Dimostrazione</a>
│
├── <a href="#panoramica-floorplan">🖼️ Panoramica Floorplan</a>
│
├── <a href="#configurazione">🛠️ Configurazione</a>
│
├── <a href="#progettazione">🎨 Progettazione</a>
│
├── <a href="#esempi-configurazione-luci">💡 Esempi Configurazione - LUCI</a>
│   ├── <a href="#switch-onoff">⬜ Switch On/Off</a>
│   ├── <a href="#cct-temperatura-colore">☀️ CCT (Temperatura Colore)</a>
│   └── <a href="#rgbcct">🎨 RGB/CCT Multi-Layer</a>
│
├── <a href="#esempi-configurazione-icone">🧩 Esempi Configurazione - ICONE</a>
│   ├── <a href="#icone-elettrodomestici">🧺 Elettrodomestici</a>
│   ├── <a href="#cover-tapparelle-finestre">🪟 Cover (Tapparelle/Finestre)</a>
│   └── <a href="#icone-tende-da-sole">🏖️ Tende da Sole</a>
│
├── <a href="#esempi-configurazione-cards">🃏 Esempi Configurazione - CARDS</a>
│   ├── <a href="#card-meteo">⛅ Card Meteo</a>
│   ├── <a href="#honeycomb-irrigazione">💧 Honeycomb Irrigazione</a>
│   ├── <a href="#potenza-istantanea">⚡ Potenza Istantanea</a>
│   └── <a href="#controllo-roborock">🧹 Controllo Roborock</a>
│
├── <a href="#pacchetti-integrati">📦 Pacchetti Integrati</a>
│   ├── <a href="#packages-elettrodomestici">⚡ Elettrodomestici</a>
│   └── <a href="#sistema-sveglie">⏰ Sistema Sveglie</a>
│
├── <a href="#finestre-popup">🎪 Finestre POPUP</a>
│   ├── <a href="#popup-elettrodomestici">⚡ Elettrodomestici</a>
│   ├── <a href="#popup-telecamere-ptz">👁️ Telecamere PTZ</a>
│   ├── <a href="#gestione-tablet">🔋 Gestione Tablet</a>
│   ├── <a href="#popup-luci-esterne">💡 Luci Esterne</a>
│   └── <a href="#controllo-tende">🕹️ Controllo Tende</a>
│
├── <a href="#template">🧩 TEMPLATE</a>
│   ├── <a href="#sensori-luce-solare">🌞 Sensori Luce Solare</a>
│   ├── <a href="#garage-virtual">🚗 Garage Virtual</a>
│   └── <a href="#giorni-raccolta">🗓️ Giorni Raccolta</a>
│
├── <a href="#contenuti-extra">🎁 Contenuti EXTRA</a>
│   ├── <a href="#pulsanti-sidebar">🌟 Pulsanti Sidebar</a>
│   └── <a href="#ventilatore-intelligente">🌀 Ventilatore Intelligente</a>
│
└── <a href="#progetti-futuri">🚧 Progetti Futuri</a>
    ├── <a href="#3d-floorplan-card">🏠 3D Floorplan</a>
    └── <a href="#wireframe-project">🏗️ Wireframe Project</a>
</pre>

**Ogni sezione include:**
• 🎬 Demo animate • ⚙️ Codice YAML • 🛠️ Requisiti tecnici
</details>

<summary><strong>📊 LEGENDA</strong></summary>

## 📊 Legenda Simboli

| Simbolo | Categoria | Descrizione |
|:-------:|-----------|-------------|
| 📹 | Media | Video dimostrativi e tutorial |
| 🖼️ | Media | Immagini, screenshot e gallery |
| ▶️ | Media | Demo animate (GIF) |
| ⚙️ | Configurazione | File YAML e setup |
| 🛠️ | Requisiti | Dipendenze e prerequisiti tecnici |
| 📚 | Documentazione | Guide e spiegazioni dettagliate |
| 📊 | Architettura | Diagrammi e strutture di sistema |
| 🎨 | Design | Elementi grafici e visual design |
| 🧩 | Componenti | Card custom e integrazioni |
| 📦 | Pacchetti | Soluzioni complete e preconfigurate |
| 🎪 | Popup | Finestre modali e overlay |
| 💡 | Luci | Configurazioni illuminazione |
| 🏠 | Casa | Automazioni domestiche |
| ⚡ | Energia | Monitoraggio consumi ed elettrodomestici |
| 🌟 | Extra | Contenuti premium e avanzati |
| 🚧 | Sviluppo | Progetti futuri e work in progress |
| ✅ | Status | Requisito obbligatorio |
| ⚠️ | Status | Requisito consigliato/opzionale |
| ❌ | Status | Non necessario |

---

### 🎯 Categorie Principali

| Categoria | Simboli Correlati | Descrizione |
|-----------|:-----------------:|-------------|
| **Illuminazione** | 💡 ☀️ 🌙 🎨 🌈 | Sistema luci con CCT, RGB e controlli avanzati |
| **Elettrodomestici** | 🧺 🌬️ 🍽️ 🔥 ⚡ | Monitoraggio consumi e automazioni |
| **Controlli** | 🪟 🏖️ 🕹️ 🎮 | Cover, tende e dispositivi meccanici |
| **Sicurezza** | 👁️ 📷 🚨 | Telecamere PTZ e sistemi allarme |
| **Clima** | ⛅ ☀️ 🌡️ 💧 | Meteo, irrigazione e temperatura |
| **Interfaccia** | 🌟 🎪 🖼️ | Sidebar, popup e elementi UI |
| **Sistema** | 🔋 📊 ⚙️ 🛠️ | Configurazione, monitoraggio e requisiti |

---

### 💫 Simboli Speciali per Stati

| Simbolo | Significato | Utilizzo |
|:-------:|-------------|----------|
| ⬜ / ⬛ | On/Off | Stati binari luci e dispositivi |
| 🟢 🟡 🔴 | Livelli consumo | Basso / Medio / Alto |
| 🔵 ⚪ | Stati speciali | Standby / Errore |
| ▲ ▼ | Movimento | Apertura / Chiusura |
| ✔️ | Completato | Ciclo terminato o stato raggiunto |

</details>
</details>

---

<details>
<h2 id="configurazione">📹 Configurazione</h2>
  <summary><strong>🛠️ Configurazione</strong></summary>

  <br>

  - **Home Assistant Core**:
    - Picture Elements Card
    - Config Template Card
    - Template Sensor
    - Template Cover
    - Script

  - **Integrazioni personalizzate (HACS)**:
    - **Essenziali** (usate in tutto il progetto):
      - button-card
      - card-mod
      - browser-mod
      - mushroom (multiple cards)
    
    - **Grafici e Visualizzazioni**:
      - mini-graph-card
      - apexcharts-card
      - bar-card
    
    - **Controlli Specifici**:
      - light-entity-card
      - slider-entity-row
      - vacuum-card
      - vertical-stack-in-card
    
    - **Utility**:
      - atomic-calendar-revive
      - weather-card
      - frigate-card
      - xiaomi-vacuum-map-card
      - hui-element

  - **Integrazioni Dispositivi**:
    - Sonoff (eWeLink)
    - EZVIZ
    - Roborock
    - Pirate Weather (o altra integrazione meteo)
</details>

---

<details>
<h2 id="progettazione">📹 Prpgettazione</h2>
  <summary><strong>🎨 Progettazione</strong></summary>

  <br>

- Progetto grafico realizzato con **Sweet_Home_3D**
- Render con **Sweet_Home_3D**
- Post-produzione e ottimizzazione immagini con **Gimp**

Le immagini finali sono ottimizzate per mantenere qualità elevata e caricamento rapido su Lovelace.
</details>

---

<details>
<h2 id="esempi-configurazione-luci">📹 💡 Esempi Configurazione - LUCI</h2>
<summary><strong>💡 Esempi di configurazione - LUCI</strong></summary>

---

<a id="-switch-onoff"></a>
<details>
<summary><strong>⬜ / ⬛ Switch on/off</strong></summary>
<br>

**Overlay Dinamico Base (switch on/off)**

<details>
<summary><strong>⚙️ MOSTRA CONFIGURAZIONE YAML</strong></summary>

```yaml
######### TAVOLO ##########

action: none
entity: light.luce_tavolo
hold_action:
action: none
image: /local/floorplan/terra/p0_tavolo.png
style:
left: 45.00%
top: 70.00%
width: 160%
height: auto
mix-blend-mode: lighten
opacity: "${states['light.luce_tavolo'].state === 'on' ? '1' : '0'}"
tap_action:
action: none
type: image
```
</details>

<details>
  <summary><strong>🛠️ REQUISITI</strong></summary>

| Componente                | File / Entità                          | Obbligatorio |
| ------------------------- | -------------------------------------- | ------------ |
| **📝 Entità YAML**        | `light.luce_tavolo`              | ✅ SÌ         |
| **📄 Immagini**           | `/local/floorplan/terra/p0_tavolo.png` | ✅ SÌ         |
| **🎨 Card nativa**        | `type: image`                          | ✅ SÌ         |

  </div>
</details>
<details>
  <summary><strong>▶️ VEDI ESEMPIO</strong></summary>

  <br>

  <div align="center">
    <img src="/www/repo/switch.gif" width="35%" alt="rgb">
  </div>

</details>

</details>
</details>

---

<details>
<summary><strong>☀️ / 🌙 Temperatura Colore Dinamica (CCT)</strong></summary>
<br>

**Simulazione realistica della temperatura (2000K–6500K) tramite filtri CSS.**

<details>
<summary><strong>⚙️ MOSTRA CONFIGURAZIONE YAML</strong></summary>

```yaml
######### CUCINA ##########

- action: none
  entity: light.cucina_windcalm_2
  hold_action:
    action: none
  image: /local/floorplan/terra/p0_cucina.png
  style:
    filter: >-
      ${(() => {
        const e = states['light.cucina_windcalm_2'].attributes;
        const kelvin = e.color_temp_kelvin || 4000;
        const ratio = (kelvin - 2000) / (6500 - 2000);
        const sepiaLevel = 1 - ratio;
        const hueRotate = (sepiaLevel - 0.5) * 30;
        const brightness = e.brightness ? e.brightness / 255 : 0.6;
        return `sepia(${sepiaLevel}) hue-rotate(${hueRotate}deg) brightness(${brightness + 0.6})`;
      })()}
    opacity: >-
      ${states['light.cucina_windcalm_2'].state === 'on'
        ? ((states['light.cucina_windcalm_2'].attributes.brightness || 180) / 255) * 1.2
        : 0}
    mix-blend-mode: lighten
    left: 45.00%
    top: 70.00%
    width: 160%
    height: auto
  tap_action:
    action: none
  type: image
```
</details>

<details>
  <summary><strong>🛠️ REQUISITI</strong></summary>

| Componente                | File / Entità                          | Obbligatorio |
| ------------------------- | -------------------------------------- | ------------ |
| **📝 Entità YAML**        | `light.cucina_windcalm_2`              | ✅ SÌ         |
| **📄 Immagini**           | `/local/floorplan/terra/p0_cucina.png` | ✅ SÌ         |
| **🎨 Card nativa**        | `type: image`                          | ✅ SÌ         |

  </div>

</details>

<details>
  <summary><strong>▶️ VEDI ESEMPIO</strong></summary>

  <br>

  <div align="center">
    <img src="/www/repo/cct.gif" width="50%" alt="rgb">
  </div>

</details>

## Caratteristiche Avanzate:

- 🎛️ Temperatura Colore Dinamica: Convertie Kelvin (2000K-6500K) in filtri CSS
- 💡 Luminosità Reale: Opacity proporzionale al brightness della luce
- 🌈 Effetti Visivi: Combinazione di sepia, hue-rotate e brightness
- 🔧 Calcolo in Tempo Reale: JavaScript inline per trasformazioni dinamiche

**Range Temperature:**

2000K (Caldo) → Sepia alto, hue-rotate negativo
4000K (Neutro) → Bilanciato
6500K (Freddo) → Sepia basso, hue-rotate positivo

</details>

---

<details>
<summary><strong>🎨🌈 Luce RGB/CCT</strong></summary>
<br>

**Sistema Multi-Layer per Luci Avanzate (Bianco, CCT, RGB).**

<details>
<summary><strong>⚙️ MOSTRA CONFIGURAZIONE YAML</strong></summary>

```yaml
######### PARENTESI - Layer 1: Base bianca ##########

action: none
entity: light.parentesi_group
hold_action:
action: none
image: /local/floorplan/transparent.png
state_image:
'on': /local/floorplan/terra/p0_parentesi.png
tap_action:
action: none
type: image
style:
opacity: >-
${ ( states["light.parentesi_group"].attributes.brightness ?
states["light.parentesi_group"].attributes.brightness / 255 : 0) -
(states["light.parentesi_group"].attributes.hs_color ?
states["light.parentesi_group"].attributes.hs_color[1]/90 : 0)}
mix-blend-mode: lighten
left: 45.00%
top: 70.00%
width: 160%

######### PARENTESI - Layer 2: CCT (bianca calda/fredda) ##########

action: none
entity: light.parentesi_group
hold_action:
action: none
image: /local/floorplan/transparent.png
state_image:
'on': /local/floorplan/terra/p0_parentesi.png
tap_action:
action: none
type: image
style:
filter: >-
${(() => {
const e = states["light.parentesi_group"].attributes;
const kelvin = e.color_temp_kelvin || 4000;
const ratio = Math.min(Math.max((kelvin - 2000) / (6500 - 2000), 0), 1);
const brightness = e.brightness ? e.brightness / 255 : 0.6;
  const sepiaLevel = 1 - ratio;
  const hueRotate = (sepiaLevel - 0.5) * 30;
  
  return `sepia(${sepiaLevel}) hue-rotate(${hueRotate}deg) brightness(${brightness + 0.1})`;
})()}
opacity: >-
${(() => {
const e = states["light.parentesi_group"].attributes;
const sat = e.hs_color ? e.hs_color[1] : 0;
if (e.color_mode !== 'hs' || sat <= 10) {
const brightness = e.brightness ? e.brightness / 255 : 0.6;
return brightness * 0.7;
}
return 0;
})()}
mix-blend-mode: lighten
left: 45.00%
top: 70.00%
width: 160%

######### PARENTESI - Layer 3: RGB (colorata) ##########

action: none
entity: light.parentesi_group
hold_action:
action: none
image: /local/floorplan/transparent.png
state_image:
'on': /local/floorplan/terra/p0_parentesirgb.png
tap_action:
action: none
type: image
style:
filter: >-
${(() => {
const e = states["light.parentesi_group"].attributes;
const hue = e.hs_color ? e.hs_color[0] : 0;
const sat = e.hs_color ? e.hs_color[1] : 0;
const bright = e.brightness ? e.brightness / 255 : 0.7;
  return `hue-rotate(${hue}deg) saturate(${sat + 20}%) brightness(${0.6 + bright * 0.6})`;
})()}
opacity: >-
${(() => {
const e = states["light.parentesi_group"].attributes;
const sat = e.hs_color ? e.hs_color[1] : 0;
   if (e.color_mode === 'hs' && sat > 10) {
    const bright = e.brightness ? e.brightness / 255 : 0.7;
    return bright;
  }
  return 0;
})()}
mix-blend-mode: lighten
left: 45.00%
top: 70.00%
width: 160%
```
</details>

<details>
  <summary><strong>🛠️ REQUISITI</strong></summary>

| Componente                | File / Entità                                | Obbligatorio |
| ------------------------- | -------------------------------------------- | ------------ |
| **📝 Entità YAML**        | `light.parentesi_group`                      | ✅ SÌ         |
| **📄 Immagini**           | `/local/floorplan/terra/p0_parentesi.png`    | ✅ SÌ         |
| **📄 Immagini**           | `/local/floorplan/terra/p0_parentesirgb.png` | ✅ SÌ         |
| **📄 Immagini**           | `/local/floorplan/transparent.png`           | ✅ SÌ         |
| **🎨 Card nativa**        | `type: image`                                | ✅ SÌ         |

  </div>

</details>

<details>
  <summary><strong>▶️ VEDI ESEMPIO</strong></summary>

  <br>

  <div align="center">
    <img src="/www/repo/rgb.gif" width="35%" alt="rgb">
  </div>

</details>

**- Questo sistema utilizza 3 layer sovrapposti, ognuno con una funzione specifica:**

- Layer 1 – Bianco Base (Brightness)
- Layer 2 – CCT (Temperatura Colore)
- Layer 3 – RGB (Colorazione)

Permette transizioni perfette tra modalità bianca, CCT e RGB.

## 🏗️ Architettura del Sistema Multi-Layer

| Modalità | Layer 1 | Layer 2 | Layer 3 |
|----------|---------|---------|---------|
| **Spento** | 0 | 0 | 0 |
| **Bianco CCT** | Alta | Media | 0 |
| **RGB Colorato** | Bassa | 0 | Alta |

## 🎯 Vantaggi dell'Approccio Multi-Layer:
1. 🎨 Gestione separata dei canali Bianco, CCT, RGB
2. ⚡ Transizioni Fluide: Nessun salto tra modalità colore
3. 🔧 Precisione Cromatica: Riproduzione fedele di temperature e tonalità
4. 🎭 Effetti Complessi: Possibilità di blending avanzato tra layer


</details>
</details>

---

<details>
<summary><strong>⭐ Esempi di configurazione - ICONE</strong></summary>

---

<details>
<summary><strong>🧺 / 🍽️ Icone elettrodomestici</strong></summary>
<br>

**Esempio di configurazione icona lavatrice con indicazione di stato e consumo**

<details>
<summary><strong>⚙️ MOSTRA CONFIGURAZIONE YAML</strong></summary>

```yaml
- type: conditional
  conditions:
    - entity: sensor.sonoff_1001d8e7f6_power_1
      state_not: "unavailable"
  elements:
    - type: custom:mushroom-chips-card
      chips:
        - type: template
          entity: switch.sonoff_1001d8e7f6_1
          icon: mdi:washing-machine
          icon_color: >
            {% set watt = states('sensor.sonoff_1001d8e7f6_power_1') | float(0) %}
            {% set is_on = is_state('switch.sonoff_1001d8e7f6_1', 'on') %}
            {% if watt > 1000 %}
              red
            {% elif watt > 300 %}
              yellow
            {% elif watt > 0 %}
              green
            {% elif is_on %}
              blue
            {% else %}
              grey
            {% endif %}
          tap_action:
            action: toggle
          hold_action:
            action: call-service
            service: script.lavatrice_popup
      alignment: justify
      style:
        top: 32.0%
        left: 76.5%
      card_mod:
        style: |
          ha-card {
            --chip-height: 60px;
          }
          mushroom-template-chip {
            --icon-size: 50px;
          }

- type: conditional
  conditions:
    - entity: sensor.sonoff_1001d8e7f6_power_1
      state_not: "unavailable"
  elements:
    - type: custom:button-card
      entity: sensor.sonoff_1001d8e7f6_power_1
      show_state: false
      show_name: false
      show_icon: false
      styles:
        card:
          - background: none
          - box-shadow: none
          - border: none
          - padding: 0
          - font-size: 12px
          - color: var(--secondary-text-color)
          - text-align: center
      custom_fields:
        consumo: >
          [[[
            const watt = parseFloat(states['sensor.sonoff_1001d8e7f6_power_1'].state) || 0;
            return watt > 0 ? watt.toFixed(0) + " W" : "";
          ]]]
      tap_action:
        action: toggle
      style:
        top: 34.0%
        left: 76.5%
```
</details>

<details>
  <summary><strong>🛠️ REQUISITI</strong></summary>

| Componente | File | Obbligatorio |
|------------|------|--------------|
| **📝 Entità YAML** | `sensor.sonoff_1001d8e7f6_power_1` | ✅ SÌ |
| **📦 packages** | `lavatrice.yaml` | ✅ SÌ |
| **🎨 Card custom** | `custom:mushroom-chips-card` | ✅ SÌ |
| **🎨 Card custom** | `custom:button-card` | ✅ SÌ |
| **🎨 Card custom** | `card-mod` | ✅ SÌ |

  </div>

</details>

<details>
  <summary><strong>🖼️ VEDI ESEMPIO</strong></summary>

  <br>

  <div align="center">
    <img src="/www/repo/elettrodomestici.png" width="35%" alt="icona">
  </div>

</details>

## 🏗️ Architettura della Card Lavatrice

**Layer 1: Stato On/Off**
- **Logica Colore**:
  - **🔴 Rosso** → consumo > 1000 W
  - **🟡 Giallo** → consumo tra 300 W e 1000 W
  - **🟢 Verde** → consumo basso tra 0 e 300 W
  - **🔵 Blu** → acceso senza consumi significativi
  - **⚪ Grigio** → spento

**Layer 2: Consumo**
- Visualizzazione watt attuali in tempo reale
- Interazione: Tap → toggle, Hold → popup informativo

## 🔄 Logica di Transizione:

| Stato | Layer 1 | Layer 2 | Layer 3 |
|-------|---------|---------|---------|
| **Spento** | ⚪ Grigio | Vuoto | Icona normale |
| **Basso consumo** | 🟢 Verde | Valore Watt | Icona normale |
| **Medio consumo** | 🟡 Giallo | Valore Watt | Icona normale |
| **Alto consumo** | 🔴 Rosso | Valore Watt | Icona normale |
| **Acceso senza consumo** | 🔵 Blu | Vuoto | Icona normale |

## 🎯 Vantaggi:
1. 🎨 Differenziazione visiva in base al consumo reale
2. ⚡ Informazioni immediate: Stato e wattaggio in un colpo d'occhio
3. 🔧 Interazione intuitiva: Tap per toggle, hold per popup
4. 🎭 Design modulare: Riutilizzabile per altri elettrodomestici

</details>

---

<details>
<summary><strong>🪟 Finestre/Tapparelle</strong></summary>
<br>

**Esempio completo per una tapparella/lucernario con:**

- **🟧 Icona dinamica** (chiusa / aperta / in movimento / errore)
- **🟦 Colorazione intelligente** (rosso = aperta, giallo = apertura, verde = chiusura, grigio = errore)
- **📊 Percentuale di apertura sotto l'icona**
- **🖱️ Tap → toggle, Hold → popup tendine**

<details>
<summary><strong>⚙️ MOSTRA CONFIGURAZIONE YAML</strong></summary>

```yaml
######### TAPPARELLA LUCERNARIO ##########

- type: custom:button-card
  entity: cover.roller_shutter_2
  show_name: false
  show_state: false
  icon: >
    [[[
      if (entity.state === 'unavailable' || entity.state === 'unknown') {
        return 'mdi:window-shutter';
      } else if (entity.state === 'open') {
        return 'mdi:window-shutter-open';
      } else if (entity.state === 'opening') {
        return 'mdi:window-shutter-open';
      } else if (entity.state === 'closing') {
        return 'mdi:window-shutter';
      } else {
        return 'mdi:window-shutter';
      }
    ]]]
  tap_action:
    action: toggle
 \
  styles:
    card:
      - background: none
      - box-shadow: none
      - border: none
      - padding: 0
      - height: 55px
      - width: 55px
    icon:
      - width: 75%
      - height: auto
      - color: >
          [[[
            if (entity.state === 'unavailable' || entity.state === 'unknown') return 'grey';
            if (entity.state === 'open') return 'var(--red-color)';
            if (entity.state === 'opening') return 'var(--yellow-color)';
            if (entity.state === 'closing') return 'var(--green-color)';
            return 'var(--secondary-text-color)';
          ]]]

  style:
    top: 70%
    left: 80%

# Percentuale tapparella
- type: custom:button-card
  entity: cover.roller_shutter_2
  show_icon: false
  show_name: false
  show_state: false
  styles:
    card:
      - background: none
      - box-shadow: none
      - border: none
      - padding: 0
      - font-size: 12px
      - color: >
          [[[
            if (entity.state === 'unavailable' || entity.state === 'unknown') return 'grey';
            return 'var(--secondary-text-color)';
          ]]]
  custom_fields:
    apertura: >
      [[[
        let state = entity.state;
        let pos = states['cover.roller_shutter_2'].attributes.current_position;
        if (state === 'unavailable' || state === 'unknown' || pos === undefined) {
          return "N/D";
        } else {
          return pos + "%";
        }
      ]]]
  style:
    top: 72.50%
    left: 80%
```
</details>

<details>
  <summary><strong>🛠️ REQUISITI</strong></summary>

| Componente         | File / Entità                                         | Obbligatorio       |
| ------------------ | ----------------------------------------------------- | ------------------ |
| **📝 Entità YAML** | `cover.roller_shutter_2`                              | ✅ SÌ               |
| **🎨 Card custom** | `custom:button-card`                                  | ✅ SÌ               |
| **🎨 Tema**        | Variabili CSS (`--red-color`, `--yellow-color`, ecc.) | ⚠️ Se non presenti |
| **📦 Packages**    | nessuno                                               | ❌ NO               |
| **📄 Immagini**    | nessuna                                               | ❌ NO               |

  </div>

</details>

<details>
  <summary><strong>▶️ VEDI ESEMPIO</strong></summary>

  <br>

  <div align="center">
    <img src="/www/repo/tapparella.gif" width="35%" alt="tenda">
  </div>

</details>

## 🏗️ Architettura della Card Tapparella

**Layer 1: Icona dinamica**
- Cambia automaticamente:
  - mdi:window-shutter → chiusa / chiusura
  - mdi:window-shutter-open → aperta / apertura

**Layer 2: Colore di stato**
- 🔴 Rosso → tapparella aperta
- 🟡 Giallo → in apertura
- 🟢 Verde → in chiusura
- ⚪ Grigio → errore, unavailable

**Layer 3: Percentuale di apertura**
- 0% → completamente chiusa
- 100% → completamente aperta
- "N/D" → se il sensore non è disponibile

## 🔄 Logica di Transizione:**

| Stato | Livello 1 | Livello 2 | Livello 3 |
|-------|-----------|-----------|-----------|
| **Chiusa** | 🪟 Icona chiusa | ⚪ Grigio | Icona normale |
| **Apertura** | 🪟 Icona aperta | 🟡 Giallo | % apertura |
| **Chiusura** | 🪟 Icona chiusa | 🟢 Verde | % apertura |
| **Aperta** | 🪟 Icona aperta | 🔴 Rosso | Icona normale |
| **N/D** | 🪟 Icona neutra | ⚪ Grigio | N/D |

## 🎯 Vantaggi:
- Monitoraggio immediato dello stato e del movimento
- Colori chiari e coerenti
- Perfetta integrazione nei floorplan
- Riutilizzabile per qualunque tapparella/tenda/velux

</details>

---

<details>
<summary><strong>🏖️ Icone Tende da sole</strong></summary>
<br>

**Questa card gestisce la tenda da sole a bracci all’interno del floorplan.**
**Mostra lo stato della tenda, la percentuale di apertura e consente il controllo diretto tramite tap/hold.**

<details>
<summary><strong>⚙️ MOSTRA CONFIGURAZIONE YAML</strong></summary>

```yaml
            ######### TENDA DA SOLE #########
            #📦 Required Packages tende.yaml#

            - type: conditional
              conditions:
                - entity: cover.tenda_a_bracci_virtual
                  state_not: "unavailable"
              elements:
                - type: custom:button-card
                  tap_action:
                    action: toggle
                    entity: cover.tenda_a_bracci_virtual
                  hold_action: !include popup/tende.yaml
                  triggers_update:
                    - entity: input_number.tende_refresher_500ms
                  show_state: false
                  show_name: false
                  show_icon: true
                  icon: mdi:awning-outline
                  styles:
                    icon:
                      - width: 45px
                      - height: 45px
                      - color: >
                          [[[ 
                            const s = states['cover.tenda_a_bracci_virtual']?.state || 'unknown';
                            if (s === 'open') return '#ff0000';
                            if (s === 'opening') return '#ffff00';
                            if (s === 'closing') return '#00ff00';
                            return '#9e9e9e';
                          ]]]
                    card:
                      - background: none
                      - box-shadow: none
                      - border: none
                      - padding: 0
                      - overflow: visible
                    custom_fields:
                      apertura:
                        - position: absolute
                        - bottom: -5px
                        - left: 50%
                        - transform: translateX(-50%)
                        - font-size: 11px
                        - font-weight: bold
                        - text-align: center
                        - text-shadow: 0px 0px 3px rgba(0,0,0,0.8)
                        - white-space: nowrap
                  custom_fields:
                    apertura: >
                      [[[
                        const s = states['cover.tenda_a_bracci_virtual']?.state || 'unknown';
                        const pos = parseFloat(states['sensor.tenda_a_bracci_percentuale_fluida']?.state || 0);
                        if (s === 'opening') return '▲ ' + pos.toFixed(0) + '%';
                        if (s === 'closing') return '▼ ' + pos.toFixed(0) + '%';
                        if (s === 'open') return '✔ ' + pos.toFixed(0) + '%';
                        return pos.toFixed(0) + '%';
                      ]]]
                  style:
                    top: 86%
                    left: 75%
```
</details>

<details>
  <summary><strong>🛠️ REQUISITI</strong></summary>

| Componente                                     | Necessario          | Note                  |
| ---------------------------------------------- | ------------------- | --------------------- |
| **`cover.tenda_a_bracci_virtual`**             | ✅                   | entità principale     |
| **`sensor.tenda_a_bracci_percentuale_fluida`** | ✅                   | percentuale fluida    |
| **`input_number.tende_refresher_500ms`**       | ⚠️ Opzionale        | refresh real-time     |
| **`custom:button-card`**                       | ✅                   | HACS richiesto        |
| **`conditional card`**                         | nativo              | nessun requisito      |
| **Popup** `popup/tende.yaml`                   | ⚠️ Se vuoi il popup | necessita browser_mod |
| **Colori tema**                                | ❌                   | usa colori fissi      |

  </div>

</details>

<details>
  <summary><strong>▶️ VEDI ESEMPIO</strong></summary>

  <br>

  <div align="center">
    <img src="/www/repo/tenda.gif" width="35%" alt="tenda">
  </div>

</details>

## 🏗️ Architettura della Card Tenda da sole

**Layer 1: Colore di stato**
- 🔴 Rosso → tenda aperta
- 🟡 Giallo → in apertura
- 🟢 Verde → in chiusura
- ⚪ Grigio → fermo/chiuso

**Layer 2: percentuale in tempo reale con:**
- ▲ = apertura + percentuale
- ▼ = chiusura + percentuale
- ✔ = aperto + percentuale
- Solo percentuale = fermo

**Interazioni:**
- Tap = toggle apertura/chiusura
- Hold = popup tende avanzato

</details>
</details>

---
<details>
<summary><strong>🃏 Esempi di configurazione - CARDS</strong></summary>

---

<details>
<summary><strong>⛅ / ☀️ Card Meteo</strong></summary>
<br>

**Esempio di configurazione card meteo**

<details>
<summary><strong>⚙️ MOSTRA CONFIGURAZIONE YAML</strong></summary>

```yaml
            - type: conditional
              conditions:
                - entity: weather.casa
                  state_not: "unavailable"
              elements:
                - type: image
                  entity: weather.casa
                  state_image:
                    "sunny": /local/weather-icons/day.svg
                    "clear-night": /local/weather-icons/night.svg
                    "partlycloudy": /local/weather-icons/partly-cloudy-day.svg
                    "cloudy": /local/weather-icons/cloudy-day-1.svg
                    "rainy": /local/weather-icons/rainy-6.svg
                  style:
                    left: 80.00%
                    top: 15.00%
                    width: 6.00%
                    height: auto
                    mix-blend-mode: lighten
                  tap_action:
                    action: none
 
            - type: state-label
              entity: weather.casa
              attribute: temperature
              style:
                left: 88.00%
                top: 15.00%
                color: white
                font-size: 40px
                font-weight: bold
                font-family: Roboto
                text-shadow: 1px 1px 2px black
              suffix: " °C"
              tap_action:
                action: none
```
</details>

<details>
  <summary><strong>🛠️ REQUISITI</strong></summary>

| Componente                         | File / Entità                | Obbligatorio               |
| ---------------------------------- | ---------------------------- | -------------------------- |
| 🌤️ **Entità meteo**               | `weather.casa`               | ✅ SÌ                       |
| 🌡️ **Temperatura (attributo)**    | `attribute: temperature`     | ✅ SÌ                       |
| 🖼️ **Icone meteo personalizzate** | `/local/weather-icons/*.svg` | ⚠️ SÌ se vuoi icone custom |
| 🧩 **Custom card**                 | Nessuna                      | ❌ NO                       |
| 🅰️ **Font**                       | Roboto                       | ⚠️ consigliato             |


  </div>

</details>

<details>
  <summary><strong>▶️ VEDI ESEMPIO</strong></summary>

  <br>

  <div align="center">
    <img src="/www/weather-icons/wind.svg" width="10%" alt="tenda">
    <img src="/www/weather-icons/clear-night.svg" width="10%" alt="tenda">
    <img src="/www/weather-icons/cloudy.svg" width="12%" alt="tenda">
    <img src="/www/weather-icons/rain.svg" width="10%" alt="tenda">
    <img src="/www/weather-icons/sleet.svg" width="10%" alt="tenda">
    <img src="/www/weather-icons/snow.svg" width="10%" alt="tenda">
    <img src="/www/weather-icons/cloudy-night-1.svg" width="15%" alt="tenda">
    <img src="/www/weather-icons/day.svg" width="15%" alt="tenda">
    <img src="/www/weather-icons/night.svg" width="15%" alt="tenda">
    <img src="/www/weather-icons/fog.svg" width="10%" alt="tenda">
  </div>

</details>

## 🌡️ Card Meteo Condizionale
Una card Home Assistant elegante che mostra le condizioni meteorologiche con:
Icona dinamica che cambia in base allo stato (sole, notte serena, nuvoloso, pioggia)
Temperatura in tempo reale visualizzata in grande con styling moderno
Design responsivo con posizionamento preciso al 80-88% della larghezza
Interattività ottimizzata - visualizzazione pulita senza azioni al tap
Effetti visivi avanzati con mix-blend-mode e text-shadow

## 🎯Funzionalità chiave:
- Si attiva solo quando weather.casa è disponibile
- Icone personalizzate nella cartella /local/weather-icons/
- Stile coerente con font Roboto e colori bilanciati

</details>

---

<details>
<summary><strong>💧 / 🚿 Honeycomb irrigazione</strong></summary>
<br>

**Esempio di configurazione card Honeycomb**

<details>
<summary><strong>⚙️ MOSTRA CONFIGURAZIONE YAML</strong></summary>

```yaml
            ######### IRRIGAZIONE ##########

            - type: image
              entity: switch.irrigazione_group
              image: /local/floorplan/transparent.png
              tap_action:
                action: call-service
                service: switch.toggle
                service_data:
                  entity_id: switch.getti_group
              hold_action:
                action: fire-dom-event
                browser_mod:
                honeycomb_menu:
                  entity:
                    - switch.sonoff_1000162117_1
                    - switch.sonoff_1000162117_2
                    - switch.sonoff_1000162117_3
                    - switch.sonoff_1000162117_4
                  buttons:
                    - icon: 'mdi:sprinkler'
                      entity: switch.sonoff_1000162117_1
                      tap_action:
                        action: toggle
                    - icon: 'mdi:sprinkler'
                      entity: switch.sonoff_1000162117_2
                      tap_action:
                        action: toggle
                    - icon: 'mdi:sprinkler-variant'
                      entity: switch.getti_group
                      tap_action:
                        action: toggle
                    - icon: 'mdi:water'
                      entity: switch.sonoff_1000162117_3                      
                      tap_action:
                        action: toggle
                    - icon: 'mdi:flower'
                      entity: switch.sonoff_1000162117_4
                      tap_action:
                        action: toggle
                    - icon: 'mdi:watering-can-outline'
                      entity: switch.irrigazione_group
                      tap_action:
                        action: toggle
              style:
                left: 69%
                top: 85%
                width: 15%
                height: 9%
                transform: |
                  translate(-55%, -100%)        /* centro */
                  rotate(-18.5deg)               /* inclinazione “di taglio” */
                  skewX(60deg)                 /* effetto parallelogramma */
                clip-path: polygon(10% 0, 90% 0, 100% 100%, 0 100%);
                # border: 1px solid red 
```
</details>

<details>
  <summary><strong>🛠️ REQUISITI</strong></summary>

| Componente                   | File / Entità                      | Obbligatorio |
| ---------------------------- | ---------------------------------- | ------------ |
| 🟢 Entità gruppo irrigazione | `switch.irrigazione_group`         | ✅            |
| 💧 Getti irrigazione         | `switch.getti_group`               | ✅            |
| 🌿 Settori individuali       | `switch.sonoff_1000162117_1-4`     | ⚠️           |
| 🧩 Integrazione              | `browser_mod`                      | ✅            |
| 🐝 Honeycomb Menu            | Configurazione browser_mod         | ⚠️           |
| 🖼️ Immagine base            | `/local/floorplan/transparent.png` | ⚠️           |
| 🧩 Custom card               | Nessuna                            | ❌            |

  </div>

</details>

<details>
  <summary><strong>▶️ VEDI ESEMPIO</strong></summary>

  <br>

  <div align="center">
    <img src="/www/repo/honeycomb.gif" width="35%" alt="irrigazione">

  </div>

</details>

## 💧 Card Irrigazione Avanzata
Una card interattiva per il controllo completo dell'impianto di irrigazione con:

## 🎯 Interazioni Multi-livello:
- Tap: Attiva/disattiva tutti i getti
- Hold: Apre menu contestuale con controllo singoli zone

## 🔧 Controlli Granulari:
- 4 zone irrigazione indipendenti (getti 1-4)
- Controllo gruppo getti
- Gestione irrigazione completa
- Icone tematiche per ogni funzione

## 🎨 Design Innovativo:
- Forma geometrica parallelogramma con trasformazioni CSS
- Posizionamento preciso con rotazione personalizzata
- Area trasparente clickabile
- Stile invisibile che si integra nel floorplan

</details>

---

<details>
<summary><strong>⚡ Card — Potenza Istantanea (Gauge Meter)</strong></summary>
<br>

Questa card mostra la potenza elettrica istantanea dell’abitazione utilizzando una gauge card personalizzata tramite hui-element.
Il colore dell’indicatore varia progressivamente in base al consumo, offrendo una rappresentazione visiva immediata e intuitiva del carico elettrico attuale.

<details>
<summary><strong>⚙️ MOSTRA CONFIGURAZIONE YAML</strong></summary>

```yaml
            ######### POTENZA ISTANTANEA ##########

            - type: custom:hui-element
              card_type: gauge
              entity: sensor.wifi_digital_meter_potenza
              name: Potenza istantanea
              min: 0
              max: 3500
              needle: true
              segments:
                - from: 0
                  color: '#4D8DF7'
                - from: 100
                  color: '#5096E5'
                - from: 200
                  color: '#53A0D3'
                - from: 300
                  color: '#57AAC2'
                - from: 400
                  color: '#5AB3B0'
                - from: 500
                  color: '#5EBD9F'
                - from: 600
                  color: '#61C78D'
                - from: 700
                  color: '#64D07B'
                - from: 800
                  color: '#68DA6A'
                - from: 900
                  color: '#6BE458'
                - from: 1000
                  color: '#6FEE47'
                - from: 1100
                  color: '#7AEF48'
                - from: 1200
                  color: '#85F149'
                - from: 1300
                  color: '#91F24A'
                - from: 1400
                  color: '#9CF44B'
                - from: 1500
                  color: '#A8F54C'
                - from: 1600
                  color: '#B3F74D'
                - from: 1700
                  color: '#BEF84E'
                - from: 1800
                  color: '#CAFA4F'
                - from: 1900
                  color: '#D5FB50'
                - from: 2000
                  color: '#E1FD52'
                - from: 2100
                  color: '#E1F050'
                - from: 2200
                  color: '#E2E44E'
                - from: 2300
                  color: '#E2D74C'
                - from: 2400
                  color: '#E3CB4A'
                - from: 2500
                  color: '#E4BE49'
                - from: 2600
                  color: '#E4B247'
                - from: 2700
                  color: '#E5A545'
                - from: 2800
                  color: '#E59943'
                - from: 2900
                  color: '#E68C41'
                - from: 3000
                  color: '#E78040'
                - from: 3100
                  color: '#E7733E'
                - from: 3200
                  color: '#E8673C'
                - from: 3300
                  color: '#E85A3A'
                - from: 3400
                  color: '#E94E38'
                - from: 3500
                  color: '#EA4237'
              hold_action:
                action: navigate
                navigation_path: /energy?kiosk
              style:
                top: 55%
                left: 12%
                width: 150px
                transform: translate(-50%, -50%)
```
</details>

<details>
  <summary><strong>🛠️ REQUISITI</strong></summary>

| Componente            | File / Entità                       | Obbligatorio |
| --------------------- | ----------------------------------- | ------------ |
| ⚡ Sensore potenza     | `sensor.wifi_digital_meter_potenza` | ✅            |
| 🧩 Custom wrapper     | `custom:hui-element`                | ✅            |
| 🖼️ Picture Elements  | Floorplan                           | ✔️           |
| 🔗 Navigazione (hold) | `/energy?kiosk`                     | ⚠️ opzionale |
| 📄 File esterni       | —                                   | ❌            |


  </div>

</details>

<details>
  <summary><strong>🖼️ VEDI ESEMPIO</strong></summary>

  <br>

  <div align="center">
    <img src="/www/repo/potenza.png" width="35%" alt="potenza">
  </div>

</details>

## 📊 Gauge dinamica

- Scala da 0 a 3500 W
- Ago attivo grazie a needle: true
- Colorazione progressiva a 36 livelli, che va:
- dal blu → consumi bassi
- al verde → consumi medi
- al giallo/arancio → consumi elevati
- al rosso → rischio sovraccarico

**Questo rende immediata la lettura del carico elettrico e della situazione energetica attuale.**

## 🖱️ Azioni

**Hold Action:**
→ Naviga automaticamente alla pagina Energia (/energy?kiosk) per una visualizzazione dettagliata dei consumi (modalità kiosk integrata).

## 🧩 Scopo della card

**Questa card fornisce una vista compatta ma estremamente informativa del consumo elettrico in tempo reale ideale per:**

- monitorare il carico istantaneo
- evitare sovraccarichi
- verificare l’attivazione di elettrodomestici energivori
- accedere rapidamente alla dashboard energetica di Home Assistant

</details>

---

<details>
<summary><strong>🧹 Card Controllo Roborock per Home Assistant</strong></summary>
<br>

**Una card personalizzata per il controllo avanzato dell'aspirapolvere Roborock Q8 Max in Home Assistant, con interfaccia visiva interattiva e mappa integrata.**

<details>
<summary><strong>⚙️ MOSTRA CONFIGURAZIONE YAML</strong></summary>

```yaml
            ######### ROBOROCK ##########
              
            - type: image
              entity: vacuum.roborock_q8_max
              state_image:
                "idle": /local/floorplan/roborock/roborockstop.gif
                "docked": /local/floorplan/roborock/roborockstop.gif
                "paused": /local/floorplan/roborock/roborockstop.gif
                "cleaning": /local/floorplan/roborock/roborock_move.gif
                "returning": /local/floorplan/roborock/roborock_move.gif
              tap_action:
                action: fire-dom-event
                browser_mod:
                  service: browser_mod.popup
                  popup_anchor: true
                  data:
                    dismissable: true
                    size: normal
                    content:
                      type: custom:mushroom-vacuum-card
                      entity: vacuum.roborock_q8_max
                      icon_animation: true
                      layout: horizontal
                      commands:
                        - start_pause
                        - on_off
                        - return_home
                        - stop
                      fill_container: true
              hold_action:
                action: fire-dom-event
                browser_mod:
                  service: browser_mod.popup
                  popup_anchor: true
                  data:
                    dismissable: true
                    size: normal
                    content:
                      type: custom:xiaomi-vacuum-map-card
                      map_source:
                        camera: camera.roborock_q8_max_map
                      calibration_source:
                        camera: true
                      entity: vacuum.roborock_q8_max
                      vacuum_platform: default
                      map_locked: true
                      two_finger_pan: true
                      map_modes:
                        - template: vacuum_clean_zone
                        - template: vacuum_goto
                        - template: vacuum_clean_segment
                          predefined_selections:
                            - id: "16"
                              icon:
                                name: mdi:broom
                                x: 28175
                                "y": 31450
                              label:
                                text: Room 16
                                x: 28175
                                "y": 31450
                                offset_y: 35
                              outline:
                                - - 25100
                                  - 29950
                                - - 31250
                                  - 29950
                                - - 31250
                                  - 32950
                                - - 25100
                                  - 32950
                            - id: "17"
                              icon:
                                name: mdi:broom
                                x: 23300
                                "y": 32175
                              label:
                                text: Room 17
                                x: 23300
                                "y": 32175
                                offset_y: 35
                              outline:
                                - - 22200
                                  - 30850
                                - - 24400
                                  - 30850
                                - - 24400
                                  - 33500
                                - - 22200
                                  - 33500
              style:
                height: auto
                left: 40.50%
                top: 78.00%
                width: 3.00%
                # border: 1px solid red
                template:
                  - vacuum
```
</details>

<details>
  <summary><strong>🛠️ REQUISITI</strong></summary>

| Componente / Integrazione                     | Necessario | Note                                                      |
| --------------------------------------------- | :--------: | --------------------------------------------------------- |
| **Vacuum entity** (`vacuum.roborock_q8_max`)  |      ✅     | Qualsiasi aspirapolvere compatibile con HA                |
| **Map camera** (`camera.roborock_q8_max_map`) |      ✅     | Necessaria per la Xiaomi Vacuum Map Card                  |
| **browser_mod**                               |      ✅     | Usato per popup tap/hold                                  |
| **Mushroom Vacuum Card**                      |      ✅     | Per il popup comandi rapidi                               |
| **Xiaomi Vacuum Map Card**                    |      ✅     | Per mappa interattiva, segmenti e zone                    |
| **GIF personalizzate**                        |     ⚠️     | Percorsi: `/local/floorplan/roborock/...`                 |
| **Templating picture-elements**               |     ⚠️     | Posizionamento dell’icona sul floorplan                   |
| **Segmenti mappa preconfigurati**             |     ⚠️     | Necessario se si vogliono le stanze cliccabili            |
| **Integrazione Roborock / Xiaomi**            |     ⚠️     | Qualsiasi metodo (ufficiale, Valetudo, Xiaomi Miot, ecc.) |

  </div>

</details>

<details>
  <summary><strong>▶️ VEDI ESEMPIO</strong></summary>

  <br>

  <div align="center">
    <img src="\www\floorplan\roborock\roborock_move.gif" width="35%" alt="potenza">
  </div>

</details>

## 🖱️ Azioni

**Tap Action:**
Apre un popup con la Mushroom Vacuum Card, che permette di avviare, fermare, mettere in pausa, spegnere e mandare l’aspirapolvere alla base.

**Hold Action:**
Apre la Xiaomi Vacuum Map Card, completa di mappa interattiva, zoom, pan a due dita e modalità avanzate:
- pulizia zona
- vai a punto specifico
- pulizia segmenti/stanze
Sono incluse numerose stanze preconfigurate con icone, label e poligoni precisi.

</details>
</details>

---

<details>
<summary><strong>🎪 Finestre POPUP</strong></summary>

---

<details>
<summary><strong>⚡ Popup elettrodomestici</strong></summary>
<br>

**Popup specializzato per il monitoraggio e controllo dell'alimentazione del tablet wall-mounted, con sistema di protezione batteria intelligente.**
<details>
  <summary><strong>🖼️ VEDI ESEMPIO</strong></summary>

  <br>

  <div align="center">
    <img src="/www/repo/lavatrice.png" width="35%" alt="popup">
  </div>

</details>

**NB: I popup elettrodomestici sono script integrati nei rispettivi packages che estendono le funzionalità dell'interfaccia principale, fornendo accesso rapido a controlli avanzati, statistiche dettagliate e strumenti di manutenzione.**

## 🎯 Caratteristiche Principali
- Script nativi: Tutti i popup sono implementati come script YAML all'interno del package stesso
- Integrazione completa: Si interfacciano perfettamente con le entità e gli automazioni del sistema
- Design modulare: Struttura a schede per una navigazione intuitiva
- Responsive: Adattabili a diverse dimensioni dello schermo

## Contenuti:
- Stato visivo con animazioni CSS personalizzate
- Timeline ultimo ciclo (inizio, fine, durata)
- Metriche economiche (consumo kWh, costo ciclo)
- Consumo istantaneo con grafico a barre animato
- Toolbar comandi per accesso rapido alle funzioni

## ⚙️ Popup Impostazioni
<details>
  <summary><strong>🖼️ VEDI ESEMPIO</strong></summary>

  <br>

  <div align="center">
    <img src="/www/repo/impo.png" width="35%" alt="impo">
  </div>

</details>
Accesso: Tramite pulsante "ingranaggio" nel popup principale

- Funzionalità:
- Controllo alimentazione elettrica
- Gestione notifiche (push e vocali)
- Configurazione costi energetici
- Monitoraggio stato manutenzioni
- Reset statistiche totali

## 📊 Popup Statistiche
Accesso: Tramite pulsante "grafico" nel popup principale

- Scheda riepilogativa: Dati testuali giornalieri/settimanali/mensili/annuali
- Grafici mensili: Consumo e costi del mese corrente
- Grafici annuali: Storico consumi e trend pluriennali
- Totali assoluti: Cicli, consumo, costo e tempo totale
<details>
  <summary><strong>▶️ VEDI ESEMPIO</strong></summary>

  <br>

  <div align="center">
    <img src="/www/repo/stats.gif" width="35%" alt="stats">
  </div>

</details>

## 🔧 Popup Manutenzione
Accesso: Tramite pulsante "tools" nel popup principale
<details>
  <summary><strong>🖼️ VEDI ESEMPIO</strong></summary>

  <br>

  <div align="center">
    <img src="/www/repo/manutenzione.png" width="90%" alt="manutenzione">
  </div>

  </details>

- Gestione programmata:
- Manutenzione Leggera (ogni 20 cicli)
- Manutenzione Standard (ogni 30 cicli)
- Manutenzione Completa (ogni 50 cicli)
- Guida operativa con istruzioni dettagliate
<details>
  <summary><strong>🖼️ VEDI ESEMPIO</strong></summary>

  <br>

  <div align="center">
    <img src="/www/repo/guida.png" width="35%" alt="guida">
  </div>

</details>

## ℹ️ Popup Informazioni
Accesso: Tramite pulsante "info" nel popup principale

- Presenta il package con:
- Descrizione funzionalità
- Link al canale YouTube
- Crediti e informazioni tecniche
<details>
  <summary><strong>🖼️ VEDI ESEMPIO</strong></summary>

  <br>

  <div align="center">
    <img src="/www/repo/info.png" width="35%" alt="info">
  </div>

</details>

**Nota Tecnica: Tutti i popup sono progettati per essere autocontenuti nel package, senza dipendenze esterne oltre alle custom card indicate nella documentazione principale.**

</details>

---

<details>
<summary><strong>👁️ Popup telecamera - Controllo PTZ e AI Integrato</strong></summary>
<br>

**Popup avanzato con controlli PTZ, streaming live e automazione AI**

<details>
<summary><strong>⚙️ MOSTRA CONFIGURAZIONE YAML</strong></summary>

```yaml
######### CAMERA GIARDINO ##########

- type: state-icon
  entity: camera.giardino
  icon: mdi:cctv
  tap_action:
    action: fire-dom-event
    browser_mod:
      service: browser_mod.popup
      data:
        title: Giardino
        dismissable: true
        size: normal
        content:
          type: custom:vertical-stack-in-card
          cards:
            - type: custom:frigate-card
              style: |
                ha-card {
                  height: 250px;
                }
              cameras:
                - camera_entity: camera.giardino
              live:
                controls:
                  ptz:
                    mode: "off"
            
            - type: custom:vertical-stack-in-card
              horizontal: true
              style: |
                ha-card {
                  padding: 8px !important;
                }
              cards:
                - type: custom:button-card
                  color_type: card
                  color: "rgba(0, 0, 0, 0.7)"
                  icon: mdi:arrow-left-drop-circle-outline
                  tap_action:
                    action: call-service
                    service: button.press
                    service_data:
                      entity_id: button.giardino_ptz_sinistra
                
                - type: custom:button-card
                  color_type: card
                  color: "rgba(0, 0, 0, 0.7)"
                  icon: mdi:arrow-up-drop-circle-outline
                  tap_action:
                    action: call-service
                    service: button.press
                    service_data:
                      entity_id: button.giardino_ptz_su
                
                - type: custom:button-card
                  color_type: card
                  color: "rgba(0, 0, 0, 0.7)"
                  icon: mdi:arrow-down-drop-circle-outline
                  tap_action:
                    action: call-service
                    service: button.press
                    service_data:
                      entity_id: button.giardino_ptz_giu
                
                - type: custom:button-card
                  color_type: card
                  color: "rgba(0, 0, 0, 0.7)"
                  icon: mdi:arrow-right-drop-circle-outline
                  tap_action:
                    action: call-service
                    service: button.press
                    service_data:
                      entity_id: button.giardino_ptz_destra
                
                - type: custom:button-card
                  entity: automation.notifica_con_ai_lettura_smart_speaker
                  color_type: card
                  icon: mdi:google-assistant
                  name: AI
                  tap_action:
                    action: call-service
                    service: automation.toggle
                    service_data:
                      entity_id: automation.notifica_con_ai_lettura_smart_speaker
                  state:
                    - value: "on"
                      color: "rgba(76, 175, 80, 0.7)"
                      icon: mdi:google
                    - value: "off"
                      color: "rgba(0, 0, 0, 0.7)"
                      icon: mdi:google
  
  hold_action:
    action: fire-dom-event
    browser_mod:
      service: browser_mod.popup
      data:
        dismissable: true
        size: normal
        content:
          type: custom:mushroom-alarm-control-panel-card
          entity: alarm_control_panel.ezviz_alarm
          states:
            - armed_home
            - armed_away
          fill_container: true
  style:
    color: '#cf07f2'
    left: 27.20%
    top: 70%
    width: 2vw
    height: 2vw
    transform: |
      translate(-50%, -50%) scaleX(-1)
      rotate(20deg)
    background-color: '#ffffff00'
    box-shadow: '0px 0px 28px 0px rgba(0,0,0,0.1)'
    border-radius: 50%
    z-index: 5
```
</details>

<details>
  <summary><strong>🛠️ REQUISITI</strong></summary>

| Componente | File / Entità | Obbligatorio |
|------------|---------------|--------------|
| 📷 Telecamera | `camera.giardino` | ✅ |
| 🎮 PTZ Sinistra | `button.giardino_ptz_sinistra` | ⚠️ |
| 🎮 PTZ Su | `button.giardino_ptz_su` | ⚠️ |
| 🎮 PTZ Giù | `button.giardino_ptz_giu` | ⚠️ |
| 🎮 PTZ Destra | `button.giardino_ptz_destra` | ⚠️ |
| 🧠 Automazione AI | `automation.notifica_con_ai_lettura_smart_speaker` | ⚠️ |
| 🚨 Allarme | `alarm_control_panel.ezviz_alarm` | ⚠️ |
| 🧩 Custom Card | `custom:frigate-card` | ⚠️ |
| 🧩 Custom Card | `custom:button-card` | ✅ |
| 🧩 Custom Card | `custom:vertical-stack-in-card` | ⚠️ |
| 🧩 Custom Card | `custom:mushroom-alarm-control-panel-card` | ⚠️ |
| 🧩 Browser Mod | `browser_mod` | ✅ |

</details>

<details>
  <summary><strong>▶️ VEDI ESEMPIO</strong></summary>

  <br>

  <div align="center">
    <img src="/www/repo/camera.gif" width="35%" alt="camera">
  </div>

</details>

## 👆 Tap - Popup Controllo Camera
- **Streaming Live**: Integrazione Frigate Card per video in tempo reale
- **Controlli PTZ**: 4 direzioni (su, giù, sinistra, destra)
- **Automazione AI**: Toggle riconoscimento con Google Gemini
- **Design Responsivo**: Layout ottimizzato mobile/tablet

## 👆 Hold - Controllo Allarme
- **Popup Secondario**: Pannello allarme EZVIZ
- **Stati Allarme**: armed_home e armed_away
- **Interfaccia Mushroom**: Design moderno

## 🔧 Componenti Integrati:

| Componente | Funzione | Custom Card |
|------------|----------|-------------|
| **Frigate** | Streaming live | custom:frigate-card |
| **Button** | Controlli PTZ | custom:button-card |
| **Mushroom** | Allarme | custom:mushroom-alarm-control-panel-card |
| **Vertical Stack** | Layout | custom:vertical-stack-in-card |

</details>

---

<details>
<summary><strong>🔋 Gestione Alimentazione Tablet</strong></summary>
<br>

**Popup specializzato per il monitoraggio e controllo dell'alimentazione del tablet wall-mounted, con sistema di protezione batteria intelligente.**
<details>
  <summary><strong>🖼️ VEDI ESEMPIO</strong></summary>

  <br>

  <div align="center">
    <img src="/www/repo/carica.png" width="35%" alt="carica">
  </div>

</details>

## ⚡ Controlli di Alimentazione

**Gestione Generale**
- input_boolean.dashboard_general_management: Toggle attivazione/disattivazione sistema

**Protezione Batteria Bassa**
- **Soglia Configurabile**: input_number.dashboard_power_battery_low - valore personalizzabile
- **Stato Attivo**: input_boolean.dashboard_power_battery_low - attivazione protezione
- **Sensore Stato**: binary_sensor.dashboard_power_battery_high - rilevamento condizione

**Protezione Batteria Alta**
- **Soglia Configurabile**: input_number.dashboard_power_battery_high - valore personalizzabile
- **Stato Attivo**: input_boolean.dashboard_power_battery_high - attivazione protezione
- **Sensore Stato**: binary_sensor.dashboard_power_battery_high - rilevamento condizione

## 📊 Monitoraggio Real-time

**Dati Batteria**
- **Livello Attuale**: sensor.my_wall_panel_battery_level - percentuale batteria in tempo reale
- **Controllo Alimentazione**: switch.sonoff_1001edb37d_2 - interruttore remoto alimentazione

**Visualizzazione Grafica**
- **Bar Card Personalizzata**: Indicatore visivo livello batteria
- **Dimensioni Ottimizzate**: 55% width, 2em height per proporzioni bilanciate
- **Formattazione Clean**: Decimali a 0 con simbolo percentuale

## 🔧 Sistema di Protezione Intelligente

**Doppia Soglia di Sicurezza**
- **Protezione Scarica Completa**: Intervento prima che batteria si esaurisca completamente
- **Protezione Sovraccarica**: Prevenzione carica eccessiva per prolungare vita batteria

**Automazioni Collegate**
- **Spegnimento Automatico**: Quando batteria raggiunge soglia minima
- **Riavvio Automatico**: Quando batteria recupera sufficiente carica
- **Notifiche Alert**: Avvisi per interventi manuali quando necessario

## 💡 Vantaggi del Sistema

**Prolungamento Vita Batteria**
- **Carica Ottimizzata**: Evita cicli di carica/scarica completi

**Affidabilità Operativa**
- **Zero Downtime**: Tablet sempre operativo quando necessario
- **Gestione Remota**: Controllo completo da qualsiasi dispositivo

</details>

---

<details>
<summary><strong>💡 Popup: Controllo Luci Esterne</strong></summary>
<br>

<details>
  <summary><strong>🖼️ VEDI ESEMPIO</strong></summary>

  <br>

  <div align="center">
    <img src="/www/repo/luci_ext.png" width="35%" alt="luci_ext">
  </div>

</details>

**Popup dedicato al controllo completo e monitoraggio del sistema di illuminazione esterna, combinando controllo manuale immediato con gestione programmazione automatica.**

## 🎨 Design e Animazioni Avanzate

**Effetti Visivi Premium**
- **Glass Morphism Avanzato**: backdrop-filter: blur(16px) brightness(0.9) per effetto vetro professionale
- **Border Moderni**: Radius 16px con bordo semitrasparente rgba(255, 255, 255, 0.1)
- **Ombre Profonde**: box-shadow: 0 0 54px 4px rgba(0, 0, 0, 0.4) per effetto di profondità

**Animazioni Fluide**
- **Fade-in Scale**: Animazione ingresso da 0.96 a 1 scale con easing
- **Transizioni Morbide**: 0.4s duration per esperienza utente premium
- **Keyframes Personalizzati**: Effetto "material design" avanzato

## 📊 Sezione Monitoraggio

**Entità Principali**
- **light.luci_esterne**: Stato luce con last-changed per ultima modifica
- **sensor.time**: Orario corrente di riferimento
- **input_datetime.orario_luci_esterne_on/off**: Orari programmati accensione/spegnimento

**Automazioni Monitorate**
- **automation.accensione_luci_esterne_orario_programmato**: Attivazione orario fisso
- **automation.spegnimento_luci_esterne_orario_programmato**: Disattivazione orario fisso
- **automation.accensione_luci_esterne_tramonto**: Attivazione sincronizzata tramonto

## 🎮 Controlli Manuali Intelligenti

**Pulsante Accensione**
- **Icona**: mdi:lightbulb-on - chiara identificazione visiva
- **Stato Dinamico**: Background attivo solo quando luce è spenta
- **Effetto Glow**: Box-shadow solo quando azione è disponibile
- **Feedback Visivo**: Colore testo che si adatta allo stato

**Pulsante Spegnimento**
- **Icona**: mdi:lightbulb-off - riconoscimento immediato
- **Stato Dinamico**: Background attivo solo quando luce è accesa
- **Effetto Glow**: Box-shadow contestuale allo stato
- ***Proporzioni**: 50% width per bilanciamento perfetto

</details>

---

<details>
<summary><strong>🕹️ Popup: Controllo Tende/Velux/tapparelle</strong></summary>
<br>

<details>
  <summary><strong>🖼️ VEDI ESEMPIO</strong></summary>

  <br>

  <div align="center">
    <img src="/www/repo/situo.png" width="35%" alt="situo">
  </div>

</details>

**Popup completamente trasparente che sovrappone un dropdown di selezione direttamente su un'immagine di sfondo, creando un'interfaccia immersiva e contestuale per il controllo delle tende.**

## 🎨 Design Trasparente Avanzato

**Rimozione Completa dello Sfondo**
- **Eliminazione Ombre**: box-shadow: none per rimuovere ogni effetto di elevazione
- **Surface Invisibile**: Dialog surface completamente trasparente

**Picture Elements Integration**
- **Immagine di Contesto**: /local/situo.png come sfondo visivo
- **Elementi Sovrapposti**: Positioning assoluto per integrazione perfetta
- **Z-index Ottimizzato**: 10 per garantire visibilità sopra l'immagine

## 💡 Caso d'Uso Innovativo

**Controllo Tendine Immersivo**
- **Selezione Visuale**: L'utente vede l'immagine della situazione reale
- **Dropdown Contestuale**: Il controllo appare nel punto logico dell'immagine
- **Esperienza Naturale**: Come interagire direttamente con la scena

</details>

</details>

---

<details>
<summary><strong>🧩 TEMPLATE</strong></summary>

---

<details>
<summary><strong>🌞 Sensori di luce solare</strong></summary>
<br>

**Questa sezione contiene template sensor utili per calcolare l’intensità luminosa in base alla posizione del sole e alla copertura nuvolosa, e un valore derivato per gestire la trasparenza o l’opacità di overlay grafici.**

<details>
<summary><strong>⚙️ MOSTRA CONFIGURAZIONE YAML</strong></summary>

```yaml
template:
  - sensor:
      - name: "Sunlight pct"
        unique_id: sunlight_pct_sensor
        state: >
          {%- set elevation = state_attr('sun.sun','elevation') | float %}
          {%- set cloud_coverage = states('sensor.pirate_weather_cloud_coverage') | float %}
          {%- set cloud_factor = (1 - (0.75 * ( cloud_coverage / 100) ** 3 )) %}
          {%- set min_elevation = -6 %}
          {%- set max_elevation = 90 %}
          {%- set adjusted_elevation = elevation - min_elevation %}
          {%- set adjusted_elevation = [adjusted_elevation,0] | max %}
          {%- set adjusted_elevation = [adjusted_elevation,max_elevation - min_elevation] | min %}
          {%- set adjusted_elevation = adjusted_elevation / (max_elevation - min_elevation) %}
          {%- set adjusted_elevation = adjusted_elevation %}
          {%- set adjusted_elevation = adjusted_elevation * 100 %}
          {%- set brightness = adjusted_elevation * cloud_factor %}
          {{ brightness | round }}
        unit_of_measurement: 'lx'
        device_class: 'illuminance'

  - sensor:
      - name: "Sunlight Opacity"
        unique_id: sensor_sunlight_opacity
        state: > 
          {%- set sunpct = states('sensor.sunlight_pct') | float %}
          {{ sunpct / 100 | float }}
```
</details>

<details>
  <summary><strong>🛠️ REQUISITI</strong></summary>

| Componente          | File / Entità                            | Obbligatorio |
| ------------------- | ---------------------------------------- | ------------ |
| **Sensori**         | `sun.sun`                                | ✅ SÌ         |
| **Sensori meteo**   | `sensor.pirate_weather_cloud_coverage`   | ✅ SÌ         |
| **Template Sensor** | `configuration.yaml` o `packages/*.yaml` | ✅ SÌ         |

</details>

## 1️⃣ Sunlight pct

- Tipo: sensor.template
- ID univoco: sunlight_pct_sensor

**Funzione: calcola la percentuale di luce solare presente in base a:**

- Elevazione del sole (sun.sun.elevation)
- Copertura nuvolosa (sensor.pirate_weather_cloud_coverage)
- Unità di misura: lux (lx)
- Device class: illuminance

## 2️⃣ Sunlight Opacity

- Tipo: sensor.template
- ID univoco: sensor_sunlight_opacity

**Funzione: restituisce un valore di opacità normalizzato tra 0 e 1, utile per regolare overlay o elementi grafici in automazioni o dashboard.**

**Calcolo:** divide la percentuale di luce solare (sensor.sunlight_pct) per 100.

</details>

---

<details>
<summary><strong> 🚗 Template/Package: Garage Virtual</strong></summary>
<br>

**Questo package gestisce un garage controllato tramite Sonoff Mini D con contatto pulito e logica inching su eWeLink. Permette di aprire/chiudere il garage automaticamente con script condizionati, e fornisce sensori virtuali per monitorare lo stato attuale.**

<details>
<summary><strong>⚙️ MOSTRA CONFIGURAZIONE YAML</strong></summary>

```yaml
script:
  open_garage:
    alias: "Apri garage"
    sequence:
      - condition: state
        entity_id: binary_sensor.garage_contact
        state: "off"   # esegue solo se CHIUSO
      - service: switch.turn_on
        target:
          entity_id: switch.sonoff_100253c202_1
    mode: single

  close_garage:
    alias: "Chiudi garage"
    sequence:
      - condition: state
        entity_id: binary_sensor.garage_contact
        state: "on"    # esegue solo se APERTO
      - service: switch.turn_on
        target:
          entity_id: switch.sonoff_100253c202_1
    mode: single


cover:
  - platform: template
    covers:
      garage_virtual:
        device_class: garage
        friendly_name: "Garage"
        value_template: "{{ is_state('binary_sensor.garage_contact', 'on') }}"
        open_cover:
          service: script.open_garage
        close_cover:
          service: script.close_garage
        icon_template: >
          {% if is_state('binary_sensor.garage_contact', 'on') %}
            mdi:garage-open
          {% else %}
            mdi:garage
          {% endif %}


template:
  - sensor:
      - name: "Stato Garage"
        unique_id: garage_state_virtual
        state: >
          {% if is_state('binary_sensor.garage_contact', 'on') %}
            Aperto
          {% else %}
            Chiuso
          {% endif %}
        icon: >
          {% if is_state('binary_sensor.garage_contact', 'on') %}
            mdi:garage-open
          {% else %}
            mdi:garage
          {% endif %}


  - trigger:
      - platform: time_pattern
        seconds: "/1"
    sensor:
      - name: "refresher_1s"
        state: "{{ now().timestamp() }}"

```
</details>

<details>
  <summary><strong>🛠️ REQUISITI</strong></summary>

| Componente                    | File / Entità                  | Obbligatorio |
| ----------------------------- | ------------------------------ | ------------ |
| **Binary sensor**             | `binary_sensor.garage_contact` | ✅ SÌ         |
| **Switch**                    | `switch.sonoff_100253c202_1`   | ✅ SÌ         |
| **Template cover**            | `cover.garage_virtual`         | ✅ SÌ         |
| **Template sensor**           | `sensor.garage_state_virtual`  | ✅ SÌ         |
| **Template sensor refresher** | `sensor.refresher_1s`          | ✅ SÌ         |

</details>

### Funzionalità principali

## Script di controllo garage
open_garage: apre il garage solo se il contatto indica che è chiuso.
close_garage: chiude il garage solo se il contatto indica che è aperto.
Gli script utilizzano switch.turn_on verso il Sonoff Mini D con logica inching attiva.

## Cover template
garage_virtual: cover virtuale con device class garage.
Valore derivato dal sensore di contatto (binary_sensor.garage_contact).
Permette apertura/chiusura tramite i servizi definiti negli script.
Icona dinamica (mdi:garage / mdi:garage-open) in base allo stato.

## Template sensor
Stato Garage: sensore virtuale che indica “Aperto” o “Chiuso” in base al contatto.
Icona dinamica che riflette lo stato del garage.

## Refresher
Sensore refresher_1s aggiornato ogni secondo tramite time_pattern.
Utile per aggiornare card o automazioni basate sullo stato del garage in tempo reale.

</details>

---

<details>
<summary><strong>🗓️ Template: Giorni Raccolta</strong></summary>
<br>

**Questa sezione contiene un template sensor che calcola quanti giorni mancano alla prossima raccolta differenziata.**

<details>
<summary><strong>⚙️ MOSTRA CONFIGURAZIONE YAML</strong></summary>

```yaml
template:
  - sensor:
      - name: "Giorni Raccolta"
        unique_id: giorni_raccolta
        state: >
          {% set next = state_attr('calendar.raccolta_differenziata', 'start_time') %}
          {% if next %}
            {{ (as_datetime(next).date() - now().date()).days }}
          {% else %}
            0
          {% endif %}
        attributes:
          tipo: "{{ state_attr('calendar.raccolta_differenziata', 'message') }}"
```
</details>

<details>
  <summary><strong>🛠️ REQUISITI</strong></summary>

| Componente          | File / Entità                            | Obbligatorio |
| ------------------- | ---------------------------------------- | ------------ |
| **Calendario**      | `calendar.raccolta_differenziata`        | ✅ SÌ         |
| **Template Sensor** | `configuration.yaml` o `packages/*.yaml` | ✅ SÌ         |

</details>

## Giorni Raccolta

- Tipo: sensor.template
- ID univoco: giorni_raccolta

## Funzione: 

- Calcola automaticamente il numero di giorni fino al prossimo evento nel calendario calendar.raccolta_differenziata.

## Logica:

- Recupera l’attributo start_time del calendario.
- Converte la data dell’evento in oggetto datetime.
- Sottrae la data corrente (now().date()) per ottenere il numero di giorni.
- Se non c’è nessun evento programmato, restituisce 0.

</details>
</details>

---

<details>
<summary><strong>📦 PACCHETTI Integrati</strong></summary>

---

<details>
<summary><strong>⚡ Packages elettrodomestici</strong></summary>
<br>

**Nella repository sono presenti i seguenti packages per il monitoraggio di elettrodomestici tradizionali**

<div align="center">
  <img src="/www/elettrodomestici/lavatrice_on.gif" width="30%" alt="🧺 Lavatrice">
  <img src="/www/elettrodomestici/asciugatrice_on.gif" width="30%" alt="🌬️ Asciugatrice">
</div>
<div align="center">
  <img src="/www/elettrodomestici/lavastoviglie_on.gif" width="30%" alt="🍽️ Lavastoviglie">
  <img src="/www/elettrodomestici/forno_on.gif" width="30%" alt="🔥 Forno">
</div>

| Icona | Elettrodomestico | Monitoraggio |
|-------|------------------|-------------|
| 🧺 | **Lavatrice** | Consumi • Costi • Cicli • Durata |
| 🌬️ | **Asciugatrice** | Consumi • Costi • Cicli • Durata |
| 🔥 | **Forno** | Consumi • Costi • Cicli • Durata |
| 🍽️ | **Lavastoviglie** | Consumi • Costi • Cicli • Durata |

**Funzionalità comuni:** 📊 Monitoraggio consumi • 💰 Calcolo costi • 🔔 Notifiche • 🔧 Manutenzione predittiva

## 🏗️ Architettura uniforme

Tutti i packages condividono la stessa struttura base e funzionalità, adattate per diversi elettrodomestici. Il sistema monitora dispositivi tradizionali attraverso prese intelligenti che tracciano esclusivamente i consumi energetici.

## ⚙️ Funzionalità Comuni a Tutti i Packages

**Monitoraggio Base**
- **Rilevamento Attività**: Identificazione accensione/spegnimento tramite soglie di consumo
- **Tracciamento Cicli**: Durata e frequenza degli utilizzi
- **Consumo Energetico**: Monitoraggio wattaggio e calcolo kWh
- **Calcolo Costi**: Conversione automatica consumo → costo

**Statistiche e Metriche**
- Utilizzi Giornalieri/Settimanali/Mensili
- Consumi Periodici e relativi costi
- Durata Media dei cicli
- Totale Cicli dall'installazione

**Sistema Notifiche**
- Alert Fine Ciclo
- Notifiche Manutenzione (basate su numero di cicli)
- Configurazione Flessibile (push, vocali, toggle)

## 🔄 Differenze Minime tra Packages

Le uniche differenze sono:
- Soglie di Consumo personalizzate per ogni elettrodomestico
- Intervalli Manutenzione specifici per tipo di dispositivo
- Nomi Entity e label personalizzate
- Icone e Temi visivi differenti

## 💡 Valore Aggiunto

Nonostante la semplicità del concetto, l'implementazione offre:
- Consapevolezza Energetica dettagliata
- Manutenzione Predittiva basata sull'utilizzo
- Automazione Notifiche contestuali
- Tracking Storico per ottimizzazioni

</details>

---

<details>
<summary><strong>⏰ Package: Sistema Sveglie Personalizzate</strong></summary>
<br>

**Sistema di sveglie avanzato che permette a più utenti di avere sveglie completamente personalizzabili con giorni della settimana selezionabili individualmente.**
<details>
  <summary><strong>🖼️ VEDI ESEMPIO</strong></summary>

  <br>

  <div align="center">
    <img src="/www/repo/sveglie.png" width="35%" alt="Sveglie">
  </div>

</details>

## 👥 Gestione Multi-Utente

**Profilo utenti**
- **Orario Sveglia**: input_datetime.sveglia_francesca_ora
- **Attivazione Globale**: input_boolean.sveglia_francesca_attiva
- **Giorni Attivi**: Toggle separati per ogni giorno della settimana

## 📅 Sistema Giorni della Settimana

**Configurazione Flessibile**
- **7 Toggle per Utente**: Controllo indipendente per ogni giorno
- **Nomi Localizzati**: Lunedì, Martedì, Mercoledì, etc.
- **Combinazioni Libere**: Possibilità di selezionare qualsiasi combinazione di giorni

## 🎵 Sistema di Allarme Musicale

**Riproduzione Media**
- **File Locali**: Riproduzione da media_source/local/
- **Brani Personalizzati** come sveglia
- **Dispositivo Target**: media_player.mansarda per la riproduzione

## 🎛️ Caratteristiche Avanzate

**Indipendenza dei Profili**
- **Orari Separati**: Ogni utente può avere orari diversi
- **Giorni Personalizzati**: Weekend e giorni feriali configurabili individualmente
- **Attivazione Indipendente**: Possibilità di disattivare temporaneamente senza perdere le impostazioni

**Gestione dei Giorni**
- **Array Giorni**: Mappatura automatica dei giorni della settimana
- **now().weekday()**: Integrazione con il sistema datetime di Home Assistant
- **Dynamic Entity Names**: Costruzione dinamica dei nomi delle entity

## 💡 Vantaggi del Sistema

**Flessibilità Totale**
- **Orari Personalizzabili**: Modifica rapida degli orari di sveglia
- **Giorni Selettivi**: Solo i giorni effettivamente necessari
- **Pause Facili**: Disattivazione temporanea mantenendo le impostazioni

**Automazione Intelligente**
- **Condizioni Multiple**: Controllo sia globale che giornaliero
- **Template Dinamici**: Adattamento automatico al giorno corrente
- **Modalità Single**: Prevenzione esecuzioni multiple

**Esperienza Utente**
- **Interfaccia Chiara**: Input boolean e datetime nativi di HA
- **Feedback Immediato**: Stato visibile nell'interfaccia
- **Facile Configurazione**: Modifica tramite la standard UI

</details>

</details>

---

<details>
<summary><strong>🎁 Contenuti EXTRA</strong></summary>

---

<details>
<summary><strong>🌟 Pulsanti SIDEBAR</strong></summary>
<br>

**I pulsanti della dashboard rappresentano l'essenza dell'approccio "Beautifully Organized" - combinano estetica premium con funzionalità avanzate, creando un'esperienza utente coerente e memorabile.**

<details>
<summary><strong>⚙️ MOSTRA CONFIGURAZIONE YAML</strong></summary>

```yaml
######### DISPOSITIVI ##########

- type: custom:button-card
  name: Dispositivi
  icon: mdi:lightbulb-group-outline
  tap_action:
    action: navigate
    navigation_path: /lovelace/0?kiosk
  style:
    top: 8.00%
    left: 12.00%
    width: 240px
    height: 45px
  layout: name_icon
  styles:
    card:
      - display: flex
      - flex-direction: row
      - justify-content: flex-start
      - align-items: center
      - background: rgba(255, 255, 255, 0.1)
      - backdrop-filter: blur(10px)
      - border: 1px solid rgba(255, 255, 255, 0.2) 
      - border-radius: 10px
      - padding: 0 24px
      - height: 100%
      - position: relative
      - overflow: hidden
    name:
      - color: white
      - font-size: 18px
      - font-weight: bold
      - margin-right: 110px
      - transform: translateY(-5px)
    icon:
      - color: white
      - width: 28px
      - height: 280px
      - margin-left: 160px
      - transform: translateY(-7px)
  card_mod:
    style: |
      ha-card {
        position: relative;
        z-index: 0;
      }
      ha-card::before {
        content: "";
        position: absolute;
        top: -4px;
        left: -4px;
        width: calc(100% + 8px);
        height: calc(100% + 8px);
        background: linear-gradient(
          45deg,
          #ff0000,
          #ff7300,
          #fffb00,
          #48ff00,
          #00ffd5,
          #002bff,
          #7a00ff,
          #ff00c8,
          #ff0000
        );
        background-size: 400%;
        z-index: -1;
        filter: blur(6px);
        border-radius: 12px;
        animation: glowing 12s linear infinite;
        opacity: 1;
      }
      ha-card::after {
        content: "";
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: #111;
        z-index: -1;
        border-radius: 10px;
      }
      @keyframes glowing {
        0% { background-position: 0 0; }
        50% { background-position: 400% 0; }
        100% { background-position: 0 0; }
      }
```
</details>

<details>
  <summary><strong>🛠️ REQUISITI</strong></summary>

| Requisito                | Necessario | Installazione   |
| ------------------------ | ---------- | --------------- |
| **Button Card**          | ✔️         | HACS → Frontend |
| **Card Mod**             | ✔️         | HACS → Frontend |

</details>

<details>
  <summary><strong>▶️ VEDI ESEMPIO</strong></summary>

  <br>

  <div align="center">
    <img src="/www/repo/pulsante.gif" width="35%" alt="Pulsante">
  </div>

</details>

## 🎨 Caratteristiche Design Avanzate

**Glass Morphism Moderno**
- **Effetto Vetro Smerigliato**: backdrop-filter: blur(10px) per profondità visiva
- **Trasparenze Controllate**: background: rgba(255, 255, 255, 0.1) per eleganza
- **Bordi Sottili**: border: 1px solid rgba(255, 255, 255, 0.2) per definizione

**Animazioni Dinamiche**
- **Gradient Animato**: Effetto arcobaleno fluido con 9 colori
- **Temporizzazione Ottimizzata**: 12 secondi per ciclo bilanciato
- **Blur Controllato**: 6px per bordo netto ma morbido
- **Background Scuro**: Contrasto perfetto per leggibilità

## 🎮 Interazione e Usabilità

**Layout Ottimizzato**
- **Flexbox Precisione**: Allineamento orizzontale perfetto
- **Spaziature Calcolate**: Margin e padding ottimizzati per touch
- **Dimensioni Consistenti**: 240px × 45px per uniformità visiva
- **Posizionamento Assoluto**: Coordinate precise nell'interfaccia

**Feedback Visivo**
- **Icone MDI**: Set coerente di icone material design
- **Tipografia Leggibile**: Font bold 18px con colore bianco
- **Consistenza**: Stile uniforme across tutti i pulsanti
- **Performance**: Animazioni smooth senza lag

## 💡 Valore Aggiunto
- **First Impression**: Impatto visivo immediato e professionale
- **Intuitività**: Icone e label auto-esplicative
- **Engagement**: Animazioni che invitano all'interazione
- **Coerenza**: Linguaggio visivo uniforme in tutta l'app

</details>

---

<details>
<summary><strong>🌀 Ventilatore intelligente</strong></summary>
<br>

**Integrazione di un ventilatore animato direttamente nel floorplan che combina visualizzazione real-time con controlli contestuali avanzati, creando un'interazione fisica virtuale unica.**

<details>
<summary><strong>⚙️ MOSTRA CONFIGURAZIONE YAML</strong></summary>

```yaml
######### VENTILATORE SOGGIORNO ##########

- type: image
  entity: fan.cucina_windcalm
  tap_action:
    action: call-service
    service: fan.toggle
    target:
      entity_id: fan.cucina_windcalm
  hold_action:
    action: fire-dom-event
    browser_mod:
      service: browser_mod.popup
      popup_anchor: true
      data:
        dismissable: true
        size: normal
        content:
          type: custom:mushroom-fan-card
          entity: fan.cucina_windcalm
          show_percentage_control: true
          show_oscillate_control: true
  style:
    top: 60.00%
    left: 58.50%
    width: 7%
    opacity: 0.3
    transform-origin: center
    transform-box: fill-box
    transform: translate(-50%, -50%)
    animation-name: rotation
    animation-duration: var(--fan-anim-duration, 1s)
    animation-timing-function: linear
    animation-iteration-count: infinite
    animation-play-state: var(--fan-anim-play, paused)
  state_image:
    "on": /local/floorplan/windcalm.png
    "off": /local/floorplan/windcalm.png
  card_mod:
    style: |
      :host {
        {% set speed = state_attr('fan.cucina_windcalm', 'percentage') | default(0) %}
        {% if is_state('fan.cucina_windcalm','on') and speed > 0 %}
          --fan-anim-duration: {{ ((100 - speed) / 40 + 0.5) | round(2) }}s;
          --fan-anim-play: running;
        {% else %}
          --fan-anim-duration: 1s;
          --fan-anim-play: paused;
        {% endif %}
      }

      @keyframes rotation {
        0%   { transform: translate(-50%, -50%) rotate(0deg); }
        100% { transform: translate(-50%, -50%) rotate(360deg); }
      }
```
</details>

<details>
  <summary><strong>🛠️ REQUISITI</strong></summary>

| Componente          | Necessario | Motivo                       |
| ------------------- | ---------- | ---------------------------- |
| **Browser_mod**     | ✔️         | Popup avanzato               |
| **Card_mod**        | ✔️         | Animazione, variabili, Jinja |
| **Mushroom**        | ✔️         | Fan card nel popup           |
| Fan standard entity | ✔️         | Per `fan.toggle`             |
| Floorplan image     | ✔️         | `state_image`                |

</details>

<details>
  <summary><strong>▶️ VEDI ESEMPIO</strong></summary>

  <br>

  <div align="center">
    <img src="/www/repo/fan.gif" width="35%" alt="fan">
  </div>

</details>

## ✨ Animazioni Dinamiche Avanzate

**Rotazione Realistica**
- **Animazione Fluida**: Rotazione 360° continua e naturale
- **Velocità Variabile**: Sync perfetto con la velocità reale del ventilatore
- **Calcolo Dinamico**: --fan-anim-duration basato sulla percentuale di velocità
- **Transform Ottimizzato**: transform-origin: center per rotazione perfetta

**Gestione Velocità**
- **Velocità Alta**: Animazione più rapida (minore duration)
- **Velocità Bassa**: Animazione più lenta (maggiore duration)
- **Range Ottimizzato**: Da 0.5s (massima velocità) a 3s (minima velocità)

## 🎮 Sistema di Interazione Multi-Livello

**Tap Action - Toggle Rapido**
- **One-Click Control**: Accensione/spegnimento immediato
- **Feedback Istantaneo**: Animazione che parte/ferma subito
- **Minimo Sforzo**: Interazione rapida per uso frequente

**Hold Action - Controllo Avanzato**
- **Popup Contextuale**: Menu controllo Mushroom design
- **Anchor Precisione**: popup_anchor: true per posizionamento ottimale
- **Controlli Granulari**:
  - Regolazione Percentuale: Controllo fine della velocità
  - Oscillazione: Toggle movimento orizzontale
  - Interfaccia Nativa: Integrazione seamless con HA

## 🎨 Design e Visual Design

**Stato Visivo Dinamico**
- **Opacità Contestuale**: 0.3 per integrazione discreta nel floorplan
- **Immagine Coerente**: Stessa immagine per stati on/off (animazione fa la differenza)
- **Posizionamento Strategico**: 60% top, 58.5% left per collocazione realistica

**Effetti di Transizione**
- **Animation State Management**: paused/running per controllo preciso
- **Transform Consistency**: translate(-50%, -50%) mantenuto durante rotazione
- **Smooth Operations**: Nessun jump o reset durante cambi di stato

</details>
</details>

---

<details>
<summary><strong>🚧 Progetti Futuri</strong></summary>

---

<details>
<summary><strong>🏠 3D Floorplan Card</strong></summary>
<br>

Uno dei miei obiettivi futuri è l'implementazione di una Floorplan 3D interattiva per la gestione completa della casa smart. Questo progetto è attualmente in fase di pianificazione e verrà realizzato non appena l'hardware a mia disposizione lo permetterà.

## 📋 Prerequisiti Necessari:

- 🖥️ Hardware più potente per gestire rendering 3D
- 🎨 Software di modellazione 3D per creare il floorplan
- 🔌 Sensori aggiuntivi per tracking preciso room-by-room
- 📡 Maggiore potenza di calcolo per elaborazione in tempo reale

## 💡 Funzionalità Previste:

- Visualizzazione 3D realistica dell'intera abitazione
- Controlli interattivi direttamente sul modello 3D
- Tracking in tempo reale di persone e dispositivi
- Overlay informazioni su stati dispositivi e sensori
- Animazioni fluide per transizioni e cambiamenti stato

</details>

---

<details>
<summary><strong>🏗️ Floorplan 3D “Wireframe Project”</strong></summary>
<br>

**Un approccio minimalista e futuristico alla visualizzazione della smart home, dove l'essenziale diventa estetico. Il wireframe non è solo una limitazione tecnica, ma una scelta di design consapevole che valorizza la struttura e le connessioni.**

<div align="center">
  <img src="/www/repo/wireframe.png" width="30%" alt="wireframe">
 </div>

## ✨ Estetica Wireframe:

- 🔷 Linee pulite e geometrie essenziali
- 🎨 Palette colori cyberpunk (blu neon, verdi elettrici)
- ✨ Effetti glow sugli elementi attivi
- 🔳 Contrasto alto per massima leggibilità

</details>

</details>
</details>