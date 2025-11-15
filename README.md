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

