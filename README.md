# SmartHome_project Floorplan
# <span style="color:#3498db">🏡 Floorplan per Home Assistant</span>

Questo progetto contiene il mio floorplan personalizzato per Home Assistant: un’interfaccia grafica avanzata basata su immagini, overlay dinamici e controlli interattivi.  
Il tutto è realizzato **in YAML**, senza moduli esterni complessi, ed è progettato per funzionare in modo fluido su tablet, dashboard wall e dispositivi touch.

L’obiettivo è creare un controllo immediato e intuitivo dell’intera casa: luci, sensori, media player, clima, consumi, porte/finestre, automazioni e molto altro.

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

<details>
<summary>🛠️ Configurazione</summary>

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

</details>

---

<details>
<summary>🎨 Design</summary>

## 🎨 Design

- Progetto grafico realizzato con **Sweet_Home_3D**
- Render con **Sweet_Home_3D**
- Post-produzione e ottimizzazione immagini con **Gimp**
Le immagini finali sono ottimizzate per mantenere qualità elevata e caricamento rapido su Lovelace.

</details>

---

<details>
<summary><strong>💡 Esempi di Configurazione - LUCI -</summary></strong>

---

<details>
<summary>⬜ / ⬛ Switch on/off</summary>

### **– Overlay Dinamico Base (switch on/off)**

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

---

<details>
<summary>☀️ / 🌙 Temperatura Colore Dinamica (CCT)</summary>

### **– Temperatura Colore Dinamica (CCT)**

Simulazione realistica della temperatura colore (2000K–6500K) tramite filtri CSS.

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

</details>

---

<details>
<summary>🎨🌈 Luce RGB/CCT</summary>

### **🌈 Luce RGB/CCT - Architettura Multi-Layer**

🌈 Sistema Multi-Layer per Luci Avanzate (Bianco, CCT, RGB)
Questo sistema utilizza 3 layer sovrapposti, ognuno con una funzione specifica:

Layer 1 – Bianco Base (Brightness)

Layer 2 – CCT (Temperatura Colore)

Layer 3 – RGB (Colorazione)

Permette transizioni perfette tra modalità bianca, CCT e RGB.

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

1. **🎨 Gestione separata**: dei canali Bianco, CCT, RGB
2. **⚡ Transizioni Fluide**: Nessun salto tra modalità colore
3. **🔧 Precisione Cromatica**: Riproduzione fedele di temperature e tonalità
4. **🎭 Effetti Complessi**: Possibilità di blending avanzato tra layer

</details>
</details>

---

<details>
<summary><strong>🧩 Esempi di configurazione - ICONE</strong></summary>

---

<details>
<summary>🧺 / 🍽️ Icone elettrodomestici</summary>

### **– Icone elettrodomestici**

Esempio di configurazione per lavatrice con indicazione stato e consumo:

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
      hold_action: !include popup/lavatrice.yaml
      style:
        top: 34.0%
        left: 76.5%
```

## 🏗️ **Architettura della Card Lavatrice**

### **Layer 1: Stato On/Off**
- **Scopo**: Mostrare se la lavatrice è accesa o spenta
- **Logica Colore**:
  - 🔴 Rosso → consumo > 1000 W
  - 🟡 Giallo → consumo tra 300 W e 1000 W
  - 🟢 Verde → consumo basso tra 0 e 300 W
  - 🔵 Blu → acceso senza consumi significativi
  - ⚪ Grigio → spento
- **Effetto**: Icona della lavatrice cambia colore in tempo reale in base ai consumi rilevati dal sensore `sensor.sonoff_1001d8e7f6_power_1`

### **Layer 2: Consumo**
- **Scopo**: Visualizzare i watt attuali
- **Attivazione**: Sempre visibile quando la card è presente e il sensore non è `unavailable`
- **Visualizzazione**:
  - Testo dinamico con `{{ watt }} W`  
  - Colore dell’icona riflette la fascia di consumo
- **Interazione**:
  - Tap → toggle accensione/spegnimento
  - Hold → popup informativo con dettagli del consumo o stato della lavatrice

### **Layer 3: Stile e Posizionamento**
- **Scopo**: Adattare l’icona e la card al floorplan
- **Parametri**:
  - `top`, `left` → posizionamento preciso sulla mappa della stanza
  - `--icon-size`, `--chip-height` → dimensioni icona e chip personalizzate
  - `alignment: justify` → allineamento visivo nella card
- **Effetto visivo**: Icona centrale con informazioni di consumo sotto o a lato, senza bordi o sfondo invasivo

## 🔄 **Logica di Transizione Intelligente**
| Stato | Layer 1 | Layer 2 | Layer 3 |
|-------|---------|---------|---------|
| **Spento** | ⚪ Grigio | Vuoto | Icona normale |
| **Basso consumo** | 🟢 Verde | Valore Watt | Icona normale |
| **Medio consumo** | 🟡 Giallo | Valore Watt | Icona normale |
| **Alto consumo** | 🔴 Rosso | Valore Watt | Icona normale |
| **Acceso senza consumo** | 🔵 Blu | Vuoto | Icona normale |

## 🎯 **Vantaggi dell’approccio multi-layer per la card**

1. **🎨 Differenziazione visiva**: Cambia colore in base al consumo reale  
2. **⚡ Informazioni immediate**: Stato e wattaggio in un colpo d’occhio  
3. **🔧 Interazione intuitiva**: Tap per toggle, hold per popup  
4. **🎭 Design modulare**: Facile da riutilizzare per altri elettrodomestici o sensori

</details>

---

<details>
<summary>🪟 / 🎚️ Icone Tende/Finestre/Tapparelle (apertura, movimento, stato)</summary>

### **– Icone cover**

Esempio completo per una tapparella/lucernario con:

🟧 Icona dinamica (chiusa / aperta / in movimento / errore)

🟦 Colorazione intelligente (rosso = aperta, giallo = apertura, verde = chiusura, grigio = errore)

📊 Percentuale di apertura sotto l'icona

🖱️ Tap → toggle, Hold → popup tendine

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
              hold_action: !include popup/tende.yaml
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
                      return "N/D";  // <-- testo mostrato quando non disponibile
                    } else {
                      return pos + "%";
                    }
                  ]]]
              style:
                top: 72.50%
                left: 80%
```
## 🏗️ Architettura della Card Tapparella
Layer 1: Icona dinamica

Scopo: Mostrare rapidamente lo stato della tapparella

Cambia automaticamente:

mdi:window-shutter → chiusa / chiusura

mdi:window-shutter-open → aperta / apertura

Icona neutra in caso di errore o stato sconosciuto

Layer 2: Colore di stato

Colorazione intelligente basata su stato:

🔴 Rosso → tapparella aperta

🟡 Giallo → in apertura

🟢 Verde → in chiusura

⚪ Grigio → errore, unavailable

Vantaggio: puoi capire a colpo d’occhio cosa sta facendo il motore

Layer 3: Percentuale di apertura

Percentuale prelevata da current_position

Mostra:

0% → completamente chiusa

100% → completamente aperta

"N/D" → se il sensore non è disponibile

Layer 4: Interazioni

Tap → toggle

Hold → popup personalizzato (popup/tende.yaml)

Nessun bordo, sfondo trasparente → perfetta per floorplan minimalisti

## 🔄 Logica di Transizione
| **Stato**             | **Livello 1**   | **Livello 2** | **Livello 3**        |
| --------------------- | --------------- | ------------- | -------------------- |
| **Chiusa**            | 🪟 Icona chiusa | ⚪ Grigio      | Icona normale        |
| **Apertura in corso** | 🪟 Icona aperta | 🟡 Giallo     | Percentuale apertura |
| **Chiusura in corso** | 🪟 Icona chiusa | 🟢 Verde      | Percentuale apertura |
| **Aperta**            | 🪟 Icona aperta | 🔴 Rosso      | Icona normale        |
| **Non disponibile**   | 🪟 Icona neutra | ⚪ Grigio      | N/D                  |

Monitoraggio immediato dello stato e del movimento

Colori chiari e coerenti con altri dispositivi (luci, lavatrice, ecc.)

Perfetta integrazione nei floorplan con Picture Elements

Completamente riutilizzabile per qualunque tapparella/tenda/velux

</details>

---

<details>
<summary>👁️ Telecamera Giardino - Controllo PTZ e AI Integrato</summary>

### **📹 Telecamera Giardino - Controllo PTZ e AI Integrato**

Icona interattiva che apre un popup avanzato con controlli PTZ, streaming live e automazione AI:

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
                # Pulsanti PTZ
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
                
                # Pulsante automazione riconoscimento con icona Gemini
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
                      color: "rgba(76, 175, 80, 0.7)"  # Verde quando attiva
                      icon: mdi:google
                    - value: "off"
                      color: "rgba(0, 0, 0, 0.7)"      # Nero quando disattiva
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

## 🎯 **Funzionalità Avanzate**

### **👆 Tap - Popup Controllo Camera**
- **Streaming Live**: Integrazione Frigate Card per video in tempo reale
- **Controlli PTZ**: 4 direzioni (su, giù, sinistra, destra) per movimento telecamera
- **Automazione AI**: Pulsante toggle per riconoscimento intelligente con Google Gemini
- **Design Responsivo**: Layout vertical stack ottimizzato per mobile/tablet

### **👆 Hold - Controllo Allarme**
- **Popup Secondario**: Accesso rapido al pannello allarme EZVIZ
- **Stati Allarme**: `armed_home` e `armed_away` per diverse modalità sicurezza
- **Interfaccia Mushroom**: Design moderno e intuitivo

## 🎨 **Stile e Posizionamento**

### **Trasformazioni CSS Avanzate:**
- **`scaleX(-1)`**: Ribaltamento orizzontale dell'icona
- **`rotate(20deg)`**: Rotazione di 20 gradi per orientamento personalizzato
- **`translate(-50%, -50%)`**: Centratura precisa della posizione

### **Design Visivo:**
- **Colore**: Viola (`#cf07f2`) per alta visibilità
- **Dimensione**: 2vw (responsive viewport width)
- **Sfondo**: Trasparente con bordi arrotondati
- **Ombra**: Sottile per effetto di profondità
- **Z-index**: 5 per sovrapposizione controllata

## 🔧 **Componenti Integrati**

| Componente | Funzione | Custom Card |
|------------|----------|-------------|
| **Frigate Card** | Streaming video live | `custom:frigate-card` |
| **Button Card** | Controlli PTZ e AI | `custom:button-card` |
| **Mushroom Alarm** | Controllo allarme | `custom:mushroom-alarm-control-panel-card` |
| **Vertical Stack** | Layout organizzato | `custom:vertical-stack-in-card` |

## ⚡ **Automazioni Collegate**

- **🤖 AI Recognition**: `automation.notifica_con_ai_lettura_smart_speaker`
- **🎮 PTZ Controls**: `button.giardino_ptz_*` (4 direzioni)
- **🚨 Allarme**: `alarm_control_panel.ezviz_alarm`

</details>
</details>

---

<details>
<summary><strong>📦 Packages Integrati</summary></strong>

---

<details>
<summary>⚡ Packages elettrodomestici</summary>

Nella repository sono presenti i seguenti packages per il monitoraggio di elettrodomestici tradizionali:

<div align="center">
  <img src="/www/elettrodomestici/lavatrice_on.gif" width="30%" alt="🧺 Lavatrice">
  <img src="/www/elettrodomestici/asciugatrice_on.gif" width="30%" alt="🌬️ Asciugatrice">
</div>
<div align="center">
  <img src="/www/elettrodomestici/lavastoviglie_on.gif" width="30%" alt="🍽️ Lavastoviglie">  
  <img src="/www/elettrodomestici/forno_on.gif" width="30%" alt="🔥 Forno">
</div>

---

| Icona | Elettrodomestico | Monitoraggio |
|-------|------------------|-------------|
| 🧺 | **Lavatrice** | Consumi • Costi • Cicli • Durata |
| 🌬️ | **Asciugatrice** | Consumi • Costi • Cicli • Durata |
| 🔥 | **Forno** | Consumi • Costi • Cicli • Durata |
| 🍽️ | **Lavastoviglie** | Consumi • Costi • Cicli • Durata |

**Funzionalità comuni:** 📊 Monitoraggio consumi • 💰 Calcolo costi • 🔔 Notifiche • 🔧 Manutenzione predittiva

## 🏗️ **Architettura uniforme**

Tutti i packages condividono la stessa struttura base e funzionalità, adattate per diversi elettrodomestici. Il sistema monitora dispositivi tradizionali attraverso prese intelligenti che tracciano esclusivamente i consumi energetici.

## **⚙️ Funzionalità Comuni a Tutti i Packages**

- **Monitoraggio Base**
- **Rilevamento Attività: Identificazione accensione/spegnimento tramite soglie di consumo**
- **Tracciamento Cicli: Durata e frequenza degli utilizzi**
- **Consumo Energetico: Monitoraggio wattaggio e calcolo kWh**
- **Calcolo Costi: Conversione automatica consumo → costo**
- **Statistiche e Metriche**
- **Utilizzi Giornalieri/Settimanali/Mensili**
- **Consumi Periodici e relativi costi**
- **Durata Media dei cicli**
- **Totale Cicli dall'installazione**
- **Sistema Notifiche**
- **Alert Fine Ciclo**
- **Notifiche Manutenzione (basate su numero di cicli)**
- **Configurazione Flessibile (push, vocali, toggle)**

## 🔄 **Differenze Minime tra Packages**

Le uniche differenze sono:
Soglie di Consumo personalizzate per ogni elettrodomestico
Intervalli Manutenzione specifici per tipo di dispositivo
Nomi Entity e label personalizzate
Icone e Temi visivi differenti

## 💡**Valore Aggiunto**
Nonostante la semplicità del concetto, l'implementazione offre:
Consapevolezza Energetica dettagliata
Manutenzione Predittiva basata sull'utilizzo
Automazione Notifiche contestuali
Tracking Storico per ottimizzazioni

</details>

---

<details>
<summary>⏰ Package: Sistema Sveglie Personalizzate</summary>
Sistema di sveglie avanzato che permette a più utenti di avere sveglie completamente personalizzabili con giorni della settimana selezionabili individualmente.

## 👥 **Gestione Multi-Utente**

# Profilo utenti
- **Orario Sveglia: input_datetime.sveglia_francesca_ora**
- **Attivazione Globale: input_boolean.sveglia_francesca_attiva**
- **Giorni Attivi: Toggle separati per ogni giorno della settimana**

## 📅 **Sistema Giorni della Settimana**

- **Configurazione Flessibile**
- **7 Toggle per Utente: Controllo indipendente per ogni giorno**
- **Nomi Localizzati: Lunedì, Martedì, Mercoledì, etc.**
- **Combinazioni Libere: Possibilità di selezionare qualsiasi combinazione di giorni**

## 🎵 **Sistema di Allarme Musicale**

- **Riproduzione Media**
- **File Locali: Riproduzione da media_source/local/**
- **Brani Personalizzati come sveglia**
- **Dispositivo Target: media_player.mansarda per la riproduzione**

## 🎛️ **Caratteristiche Avanzate**
- **Indipendenza dei Profili**
- **Orari Separati: Ogni utente può avere orari diversi**
- **Giorni Personalizzati: Weekend e giorni feriali configurabili individualmente**
- **Attivazione Indipendente: Possibilità di disattivare temporaneamente senza perdere le impostazioni**

# **Gestione dei Giorni**
- **Array Giorni: Mappatura automatica dei giorni della settimana**
- **now().weekday(): Integrazione con il sistema datetime di Home Assistant**
- **Dynamic Entity Names: Costruzione dinamica dei nomi delle entity**

## 💡 **Vantaggi del Sistema**
- **Flessibilità Totale**
- **Orari Personalizzabili: Modifica rapida degli orari di sveglia**
- **Giorni Selettivi: Solo i giorni effettivamente necessari**
- **Pause Facili: Disattivazione temporanea mantenendo le impostazioni**

# **Automazione Intelligente**
- **Condizioni Multiple: Controllo sia globale che giornaliero**
- **Template Dinamici: Adattamento automatico al giorno corrente**
- **Modalità Single: Prevenzione esecuzioni multiple**

# **Esperienza Utente**
- **Interfaccia Chiara: Input boolean e datetime nativi di HA**
- **Feedback Immediato: Stato visibile nell'interfaccia**
- **Facile Configurazione: Modifica tramite la standard UI**

</details>
</details>

---

<details>
<summary><strong>🎪 Finestre popup integrate</summary></strong>


---

<details>
<summary>🔋 Gestione Alimentazione Tablet</summary>

Popup specializzato per il monitoraggio e controllo dell'alimentazione del tablet wall-mounted, con sistema di protezione batteria intelligente.

## 🎨 **Design Avanzato**
- **Effetti Visivi Premium**
- **Glass Morphism: Sfondo con backdrop-filter: blur(15px) per effetto vetro smerigliato**
- **Trasparenze Controllate: background-color: rgba(25, 25, 25, 0.5) per profondità**
- **Border Radius Moderni: Angoli arrotondati da 1em per design contemporaneo**
- **Ombre Soft: box-shadow con rgba per effetto di elevazione sottile**

## **Header Personalizzato**
- **Logo/Custom Image: Immagine "galaxy.png" come identificativo visivo**
- **Pulsante Chiudi Custom: Icona MDI con styling minimale e allineamento perfetto**
- **Layout Flex: Giustificazione spaziata per bilanciamento ottimale**

## ⚡ **Controlli di Alimentazione**
- **Gestione Generale**
- **input_boolean.dashboard_general_management: Toggle attivazione/disattivazione sistema**
- **Protezione Batteria Bassa**
- **Soglia Configurabile: input_number.dashboard_power_battery_low - valore personalizzabile**
- **Stato Attivo: input_boolean.dashboard_power_battery_low - attivazione protezione**
- **Sensore Stato: binary_sensor.dashboard_power_battery_high - rilevamento condizione**
- **Protezione Batteria Alta**
- **Soglia Configurabile: input_number.dashboard_power_battery_high - valore personalizzabile**
- **Stato Attivo: input_boolean.dashboard_power_battery_high - attivazione protezione**
- **Sensore Stato: binary_sensor.dashboard_power_battery_high - rilevamento condizione**

## 📊 **Monitoraggio Real-time**
# Dati Batteria
- **Livello Attuale: sensor.my_wall_panel_battery_level - percentuale batteria in tempo reale**
- **Controllo Alimentazione: switch.sonoff_1001edb37d_2 - interruttore remoto alimentazione**

# Visualizzazione Grafica
- **Bar Card Personalizzata: Indicatore visivo livello batteria**
- **Dimensioni Ottimizzate: 55% width, 2em height per proporzioni bilanciate**
- **Formattazione Clean: Decimali a 0 con simbolo percentuale**

## 🔧 **Sistema di Protezione Intelligente**
# Doppia Soglia di Sicurezza
- **Protezione Scarica Completa: Intervento prima che batteria si esaurisca completamente**
- **Protezione Sovraccarica: Prevenzione carica eccessiva per prolungare vita batteria**

# Automazioni Collegate
- **Spegnimento Automatico: Quando batteria raggiunge soglia minima**
- **Riavvio Automatico: Quando batteria recupera sufficiente carica**
- **Notifiche Alert: Avvisi per interventi manuali quando necessario**

## 🎛️ **Caratteristiche Tecniche**
# Gestione Stato
- **Input Boolean: Configurazione comportamenti protezione**
- **Input Number: Soglie personalizzabili per diversi scenari d'uso**
- **Binary Sensor: Rilevamento stati critici in tempo reale**
- **Integrazione Hardware**
- **Tablet Wall-Mounted: Dispositivo principale monitorato**
- **Presa Smart: Controllo remoto alimentazione**
- **Sensori Batteria: Integrazione con sistema operativo tablet**

## 💡 **Vantaggi del Sistema**
- **Prolungamento Vita Batteria**
- **Carica Ottimizzata: Evita cicli di carica/scarica completi**
- **Affidabilità Operativa**
- **Zero Downtime: Tablet sempre operativo quando necessario**
- **Gestione Remota: Controllo completo da qualsiasi dispositivo**

</details>

---

<details>
<summary>💡 Popup: Controllo Luci Esterne</summary>

Popup dedicato al controllo completo e monitoraggio del sistema di illuminazione esterna, combinando controllo manuale immediato con gestione programmazione automatica.

## 🎨 **Design e Animazioni Avanzate**
# Effetti Visivi Premium
- **Glass Morphism Avanzato: backdrop-filter: blur(16px) brightness(0.9) per effetto vetro professionale**
- **Border Moderni: Radius 16px con bordo semitrasparente rgba(255, 255, 255, 0.1)**
- **Ombre Profonde: box-shadow: 0 0 54px 4px rgba(0, 0, 0, 0.4) per effetto di profondità**

## Animazioni Fluide
- **Fade-in Scale: Animazione ingresso da 0.96 a 1 scale con easing**
- **Transizioni Morbide: 0.4s duration per esperienza utente premium**
- **Keyframes Personalizzati: Effetto "material design" avanzato**

## 📊 **Sezione Monitoraggio**
# Entità Principali
- **light.luci_esterne: Stato luce con last-changed per ultima modifica**
- **sensor.time: Orario corrente di riferimento**
- **input_datetime.orario_luci_esterne_on/off: Orari programmati accensione/spegnimento**

## Automazioni Monitorate
- **automation.accensione_luci_esterne_orario_programmato: Attivazione orario fisso**
- **automation.spegnimento_luci_esterne_orario_programmato: Disattivazione orario fisso**
- **automation.accensione_luci_esterne_tramonto: Attivazione sincronizzata tramonto**

## 🎮 **Controlli Manuali Intelligenti**
# Pulsante Accensione
- **Icona: mdi:lightbulb-on - chiara identificazione visiva**
- **Stato Dinamico: Background attivo solo quando luce è spenta**
- **Effetto Glow: Box-shadow solo quando azione è disponibile**
- **Feedback Visivo: Colore testo che si adatta allo stato**

# Pulsante Spegnimento
- **Icona: mdi:lightbulb-off - riconoscimento immediato**
- **Stato Dinamico: Background attivo solo quando luce è accesa**
- **Effetto Glow: Box-shadow contestuale allo stato**
- **Proporzioni: 50% width per bilanciamento perfetto**

</details>

---

<details>
<summary>🕹️ Popup: Controllo Tende/Velux/tapparelle</summary>

## 🎮 **Telecomando Tende/Velux/tapparelle Trasparente**
Popup completamente trasparente che sovrappone un dropdown di selezione direttamente su un'immagine di sfondo, creando un'interfaccia immersiva e contestuale per il controllo delle tende.

## 🎨 **Design Trasparente Avanzato**
- **Rimozione Completa dello Sfondo**
- **Eliminazione Ombre: box-shadow: none per rimuovere ogni effetto di elevazione**
- **Surface Invisibile: Dialog surface completamente trasparente**
- **Picture Elements Integration**
- **Immagine di Contesto: /local/situo.png come sfondo visivo**
- **Elementi Sovrapposti: Positioning assoluto per integrazione perfetta**
- **Z-index Ottimizzato: 10 per garantire visibilità sopra l'immagine**

## 💡 **Caso d'Uso Innovativo**
- **Controllo Tendine Immersivo**
- **Selezione Visuale: L'utente vede l'immagine della situazione reale**
- **Dropdown Contestuale: Il controllo appare nel punto logico dell'immagine**
- **Esperienza Naturale: Come interagire direttamente con la scena**

</details>
</details>

---

<details>
<summary><strong>🎁 Contenuti EXTRA</summary></strong>


---

<details>
<summary>🌟 Pusanti SIDEBAR</summary>
I pulsanti della dashboard rappresentano l'essenza dell'approccio "Beautifully Organized" - combinano estetica premium con funzionalità avanzate, creando un'esperienza utente coerente e memorabile.

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
                    filter: blur(6px);   /* meno sfocato → bordo più netto */
                    border-radius: 12px;
                    animation: glowing 12s linear infinite; /* più veloce */
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
## 🎨 **Caratteristiche Design Avanzate**
- **Glass Morphism Moderno**
- **Effetto Vetro Smerigliato: backdrop-filter: blur(10px) per profondità visiva**
- **Trasparenze Controllate: background: rgba(255, 255, 255, 0.1) per eleganza**
- **Bordi Sottili: border: 1px solid rgba(255, 255, 255, 0.2) per definizione**

## **Animazioni Dinamiche**
- **Gradient Animato: Effetto arcobaleno fluido con 9 colori**
- **Temporizzazione Ottimizzata: 12 secondi per ciclo bilanciato**
- **Blur Controllato: 6px per bordo netto ma morbido**
- **Background Scuro: Contrasto perfetto per leggibilità**

## 🎮 **Interazione e Usabilità**
- **Layout Ottimizzato**
- **Flexbox Precisione: Allineamento orizzontale perfetto**
- **Spaziature Calcolate: Margin e padding ottimizzati per touch**
- **Dimensioni Consistenti: 240px × 45px per uniformità visiva**
- **Posizionamento Assoluto: Coordinate precise nell'interfaccia**
- **Feedback Visivo**
- **Icone MDI: Set coerente di icone material design**
- **Tipografia Leggibile: Font bold 18px con colore bianco**
- **Consistenza: Stile uniforme across tutti i pulsanti**
- **Performance: Animazioni smooth senza lag**

## **Customizzazione**
- **Temi Dinamici: Adattamento a light/dark mode**
- **Varianti Colore: Palette coerente ma distinguibile**
- **Scalabilità: Adattamento a diverse risoluzioni**

## 💡 **Valore Aggiunto**
- **First Impression: Impatto visivo immediato e professionale**
- **Intuitività: Icone e label auto-esplicative**
- **Engagement: Animazioni che invitano all'interazione**
- **Coerenza: Linguaggio visivo uniforme in tutta l'app**

</details>

---

<details>
<summary>🌀 Ventilatore intelligente</summary>
Integrazione di un ventilatore animato direttamente nel floorplan che combina visualizzazione real-time con controlli contestuali avanzati, creando un'interazione fisica virtuale unica.

<div align="center">

[**⚙️ Mostra Configurazione YAML**]

</div>

<!-- Contenuto nascosto che appare al click -->
<div id="yaml-config" style="display: none;">

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
                      /* Pausa l'animazione, niente salti/shift dell'immagine */
                      --fan-anim-duration: 1s;
                      --fan-anim-play: paused;
                    {% endif %}
                  }
            
                  @keyframes rotation {
                    0%   { transform: translate(-50%, -50%) rotate(0deg); }
                    100% { transform: translate(-50%, -50%) rotate(360deg); }
                  }
```

</div>

## ✨ **Animazioni Dinamiche Avanzate**
- **Rotazione Realistica**
- **Animazione Fluida: Rotazione 360° continua e naturale**
- **Velocità Variabile: Sync perfetto con la velocità reale del ventilatore**
- **Calcolo Dinamico: --fan-anim-duration basato sulla percentuale di velocità**
- **Transform Ottimizzato: transform-origin: center per rotazione perfetta**
- **Velocità Alta: Animazione più rapida (minore duration)**
- **Bassa: Animazione più lenta (maggiore duration)**
- **Range Ottimizzato: Da 0.5s (massima velocità) a 3s (minima velocità)**

## 🎮 **Sistema di Interazione Multi-Livello**
- **Tap Action - Toggle Rapido**
- **One-Click Control: Accensione/spegnimento immediato**
- **Feedback Istantaneo: Animazione che parte/ferma subito**
- **Minimo Sforzo: Interazione rapida per uso frequente**
- **Hold Action - Controllo Avanzato**
- **Popup Contextuale: Menu controllo Mushroom design**
- **Anchor Precisione: popup_anchor: true per posizionamento ottimale**
- **Controlli Granulari:**
- **Regolazione Percentuale: Controllo fine della velocità**
- **Oscillazione: Toggle movimento orizzontale**
- **Interfaccia Nativa: Integrazione seamless con HA**

## 🎨 **Design e Visual Design**
- **Stato Visivo Dinamico**
- **Opacità Contestuale: 0.3 per integrazione discreta nel floorplan**
- **Immagine Coerente: Stessa immagine per stati on/off (animazione fa la differenza)**
- **Posizionamento Strategico: 60% top, 58.5% left per collocazione realistica**
- **Effetti di Transizione**
- **Animation State Management: paused/running per controllo preciso**
- **Transform Consistency: translate(-50%, -50%) mantenuto durante rotazione**
- **Smooth Operations: Nessun jump o reset durante cambi di stato**
</details>