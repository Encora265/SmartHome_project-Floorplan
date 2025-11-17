# SmartHome_project Floorplan
# <span style="color:#3498db">🏡 Floorplan per Home Assistant</span>

Questo progetto contiene il mio floorplan personalizzato per Home Assistant: un'interfaccia grafica avanzata basata su immagini, overlay dinamici e controlli interattivi.
Il tutto è realizzato **in YAML**, senza moduli esterni complessi, ed è progettato per funzionare in modo fluido su tablet, dashboard wall e dispositivi touch.

L'obiettivo è creare un controllo immediato e intuitivo dell'intera casa: luci, sensori, media player, clima, consumi, porte/finestre, automazioni e molto altro.

---

## 🎥 Dimostrazione

[![Demo Floorplan](https://github.com/Encora265/SmartHome_project-Floorplan/blob/main/demo.gif)](https://www.youtube.com/watch?v=25UP5QQ9EAA&t=355s)

> ⚠️ Nota: alcune funzionalità mostrate nel video potrebbero differire leggermente dalla versione attuale del repository.

---

## 🖼️ Panoramica del Floorplan

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

---

## 🛠️ Configurazione

<details>
<summary>Clicca per vedere i dettagli</summary>

- **Home Assistant**:
  - Picture Elements Card
  - Config Template Card

- **Integrazioni personalizzate (HACS)**:
  - button-card
  - light-entity-card
  - mini-graph-card
  - vertical-stack-in-card
  - slider-entity-row
  - apexcharts-card
  - atomic-calendar-revive
  - vacuum-card
  - weather-card
  - ...e altre

</details>

---

## 🎨 Progettazione

<details>
<summary>Clicca per vedere i dettagli</summary>

- Progetto grafico realizzato con **Sweet_Home_3D**
- Render con **Sweet_Home_3D**
- Post-produzione e ottimizzazione immagini con **Gimp**

Le immagini finali sono ottimizzate per mantenere qualità elevata e caricamento rapido su Lovelace.

</details>

---

## 💡 Esempi di configurazione - LUCI

<details>
<summary><strong>Clicca per vedere tutti gli esempi</strong></summary>

### ⬜ / ⬛ Switch on/off

<details>
<summary>Mostra dettagli</summary>

**– Overlay Dinamico Base (switch on/off)**

<details>
<summary><strong>⚙️ MOSTRA CONFIGURAZIONE YAML</strong></summary>

```yaml
######### TAVOLO ##########

- action: none
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

</details>

---

### ☀️ / 🌙 Temperatura Colore Dinamica (CCT)

<details>
<summary>Mostra dettagli</summary>

**– Temperatura Colore Dinamica (CCT)**

Simulazione realistica della temperatura colore (2000K–6500K) tramite filtri CSS.

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

**Caratteristiche Avanzate:**
- **🎛️ Temperatura Colore Dinamica**: Convertie Kelvin (2000K-6500K) in filtri CSS
- **💡 Luminosità Reale**: Opacity proporzionale al brightness della luce
- **🌈 Effetti Visivi**: Combinazione di sepia, hue-rotate e brightness
- **🔧 Calcolo in Tempo Reale**: JavaScript inline per trasformazioni dinamiche

**Range Temperature:**
- **2000K** (Caldo) → Sepia alto, hue-rotate negativo
- **4000K** (Neutro) → Bilanciato
- **6500K** (Freddo) → Sepia basso, hue-rotate positivo

</details>

---

### 🎨🌈 Luce RGB/CCT

<details>
<summary>Mostra dettagli</summary>

**🌈 Luce RGB/CCT - Architettura Multi-Layer**

Sistema Multi-Layer per Luci Avanzate (Bianco, CCT, RGB).
Questo sistema utilizza 3 layer sovrapposti, ognuno con una funzione specifica:

- Layer 1 – Bianco Base (Brightness)
- Layer 2 – CCT (Temperatura Colore)
- Layer 3 – RGB (Colorazione)

Permette transizioni perfette tra modalità bianca, CCT e RGB.

<details>
<summary><strong>⚙️ MOSTRA CONFIGURAZIONE YAML</strong></summary>

```yaml
######### PARENTESI - Layer 1: Base bianca ##########

- action: none
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

- action: none
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

- action: none
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

**🏗️ Architettura del Sistema Multi-Layer**

| Modalità | Layer 1 | Layer 2 | Layer 3 |
|----------|---------|---------|---------|
| **Spento** | 0 | 0 | 0 |
| **Bianco CCT** | Alta | Media | 0 |
| **RGB Colorato** | Bassa | 0 | Alta |

**🎯 Vantaggi:**
1. 🎨 Gestione separata dei canali Bianco, CCT, RGB
2. ⚡ Transizioni Fluide
3. 🔧 Precisione Cromatica
4. 🎭 Effetti Complessi

</details>

</details>

---

## 🧩 Esempi di configurazione - ICONE

<details>
<summary><strong>Clicca per vedere tutti gli esempi</strong></summary>

### 🧺 / 🍽️ Icone elettrodomestici

<details>
<summary>Mostra dettagli</summary>

Esempio di configurazione per lavatrice con indicazione stato e consumo.

[... contenuto icone elettrodomestici ...]

</details>

---

### 🪟 / 🎚️ Icone Tende/Finestre/Tapparelle

<details>
<summary>Mostra dettagli</summary>

[... contenuto icone cover ...]

</details>

---

### 👁️ Telecamera Giardino

<details>
<summary>Mostra dettagli</summary>

[... contenuto telecamera ...]

</details>

</details>

---

## 📦 Pacchetti Integrati

<details>
<summary><strong>Clicca per vedere tutti i pacchetti</strong></summary>

### ⚡ Packages elettrodomestici

<details>
<summary>Mostra dettagli</summary>

[... contenuto packages elettrodomestici ...]

</details>

---

### ⏰ Package: Sistema Sveglie Personalizzate

<details>
<summary>Mostra dettagli</summary>

[... contenuto sveglie ...]

</details>

</details>

---

## 🎪 Finestre popup integrate

<details>
<summary><strong>Clicca per vedere tutti i popup</strong></summary>

### 🔋 Gestione Alimentazione Tablet

<details>
<summary>Mostra dettagli</summary>

[... contenuto popup tablet ...]

</details>

---

### 💡 Popup: Controllo Luci Esterne

<details>
<summary>Mostra dettagli</summary>

[... contenuto popup luci esterne ...]

</details>

---

### 🕹️ Popup: Controllo Tende/Velux/tapparelle

<details>
<summary>Mostra dettagli</summary>

[... contenuto popup tende ...]

</details>

</details>

---

## 🎁 Contenuti EXTRA

<details>
<summary><strong>Clicca per vedere i contenuti extra</strong></summary>

### 🌟 Pulsanti SIDEBAR

<details>
<summary>Mostra dettagli</summary>

[... contenuto sidebar ...]

</details>

---

### 🌀 Ventilatore intelligente

<details>
<summary>Mostra dettagli</summary>

[... contenuto ventilatore ...]

</details>

</details>