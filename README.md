# SmartHome_project Floorplan
# 🏡 Floorplan per Home Assistant

Questo progetto contiene il mio floorplan personalizzato per Home Assistant, realizzato interamente in YAML e ottimizzato per un'interfaccia moderna, fluida e altamente reattiva.

Il floorplan combina immagini, overlay dinamici e animazioni per rappresentare graficamente lo stato della casa: luci, sensori, clima, consumi, porte/finestre e molto altro.

L'obiettivo è offrire un controllo intuitivo e immediato dell'abitazione, integrandosi perfettamente con Lovelace e supportando dispositivi RGB, CCT, dimmer, gruppi e automazioni avanzate.

Il progetto è pensato per essere scalabile, modulare e facilmente riutilizzabile, con esempi pronti all'uso per ogni tipologia di entità.

---

## 🎥 Dimostrazione

[![Demo Floorplan](https://github.com/Encora265/SmartHome_project-Floorplan/blob/main/demo.gif)](https://www.youtube.com/watch?v=25UP5QQ9EAA&t=355s)

> ⚠️ Nota: alcune funzionalità mostrate nel video potrebbero differire leggermente dalla versione attuale del repository.

---

## 🖼️ Panoramica del Floorplan

Il design è stato realizzato con un approccio visivo pulito e moderno, ottimizzato per l'uso su tablet o schermi wall-mounted.

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

---

## 🎨 Design

- Progetto grafico realizzato con **Sweet_Home_3D**
- Render con **Sweet_Home_3D**
- Post-produzione e ottimizzazione immagini con **Gimp**


---

### **Configurazione Luce Tavolo**

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
### **🎨 Luce Cucina - Effetto Temperatura Colore Dinamico**

Elemento avanzato che replica dinamicamente la temperatura colore Kelvin della luce:

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

**Caratteristiche Avanzate:**
- **🎛️ Temperatura Colore Dinamica**: Convertie Kelvin (2000K-6500K) in filtri CSS
- **💡 Luminosità Reale**: Opacity proporzionale al brightness della luce
- **🌈 Effetti Visivi**: Combinazione di sepia, hue-rotate e brightness
- **🔧 Calcolo in Tempo Reale**: JavaScript inline per trasformazioni dinamiche

**Range Temperature:**
- **2000K** (Caldo) → Sepia alto, hue-rotate negativo
- **4000K** (Neutro) → Bilanciato
- **6500K** (Freddo) → Sepia basso, hue-rotate positivo

### **🌈 Sistema Luce Parentesi - Architettura Multi-Layer**

Configurazione avanzata che utilizza **tre layer sovrapposti** per gestire separatamente bianco, CCT e RGB:

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
    'on': /local/floorplan/terra/p0_parentesi.png  # immagine BIANCA
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
        
        // Caldo (2000K) = giallo/arancio, Freddo (6500K) = blu
        const sepiaLevel = 1 - ratio;  // 1 per caldo, 0 per freddo
        const hueRotate = (sepiaLevel - 0.5) * 30;  // ±15°
        
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
    'on': /local/floorplan/terra/p0_parentesirgb.png  # immagine ROSSA/COLORATA
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

## 🏗️ **Architettura del Sistema Multi-Layer**

### **Layer 1: Base Bianca**
- **Scopo**: Fornire la luminosità base quando la luce è accesa
- **Logica Opacity**: 
  - `brightness/255` → intensità proporzionale
  - `- hs_color[1]/90` → riduce opacità quando c'è saturazione colore
- **Effetto**: Bianco puro che si attenua quando si attiva RGB

### **Layer 2: Temperatura Colore (CCT)**
- **Scopo**: Gestire le tonalità calde/fredde (2000K-6500K)
- **Attivazione**: Solo quando `color_mode ≠ 'hs'` o saturazione ≤ 10
- **Filtri Dinamici**:
  - **Sepia**: Alto per caldo (2000K), basso per freddo (6500K)
  - **Hue Rotate**: Regolato per enfatizzare caldo/freddo
  - **Brightness**: Basato sull'intensità reale della luce

### **Layer 3: Colore RGB**
- **Scopo**: Gestire la saturazione e tonalità colore
- **Attivazione**: Solo quando `color_mode = 'hs'` e saturazione > 10
- **Filtri Avanzati**:
  - **Hue Rotate**: Replica esattamente la tonalità HSV della luce
  - **Saturate**: Aumenta saturazione base (+20%) per effetto più vibrante
  - **Brightness**: Combinazione di base + intensità dinamica

## 🔄 **Logica di Transizione Intelligente**

| Modalità | Layer 1 | Layer 2 | Layer 3 |
|----------|---------|---------|---------|
| **Spento** | 0 | 0 | 0 |
| **Bianco CCT** | Alta | Media | 0 |
| **RGB Colorato** | Bassa | 0 | Alta |

## 🎯 **Vantaggi dell'Approccio Multi-Layer**

1. **🎨 Separazione dei Canali**: Bianco, CCT e RGB gestiti indipendentemente
2. **⚡ Transizioni Fluide**: Nessun salto tra modalità colore
3. **🔧 Precisione Cromatica**: Riproduzione fedele di temperature e tonalità
4. **🎭 Effetti Complessi**: Possibilità di blending avanzato tra layer

**Questa è una delle configurazioni più avanzate che abbia visto!** Mostra una profonda comprensione della gestione colore in Home Assistant. 🚀
