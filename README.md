# ⚔️ Buscamines del Regne Malaït

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Figma](https://img.shields.io/badge/Figma-F24E1E?style=for-the-badge&logo=figma&logoColor=white)

> Joc Buscamines per a dispositius mòbils amb ambientació modern-medieval, mecànica de risc pròpia i rànquing global. Projecte intermodular DAW/DAM 2025/2026.

---

## 📖 Descripció

**Buscamines del Regne Malaït** és un joc d'un sol jugador dissenyat especialment per a mòbil. Manté la mecànica clàssica del Buscamines —descobrir caselles sense activar trampes— però afegeix una capa d'estratègia i tensió única: **l'Ampliació Maleïda**.

Un cop superat un tauler, el jugador pot decidir si recull els punts de forma segura o s'arrisca a ampliar el tauler per doblar la puntuació. Una trampa ho perd tot. D'aquí ve el nom: **el Regne Malaït**.

---

## ⚙️ Tecnologies utilitzades

| Tecnologia | Ús al projecte |
|---|---|
| **HTML5 / CSS3** | Estructura i maquetació de la interfície web, disseny responsive per a mòbil |
| **JavaScript** | Lògica del joc: generació del tauler, detecció de trampes, cronòmetre i sistema de puntuació |
| **SQL** | Disseny de la base de dades relacional: jugadors, nivells, partides i rànquing global |
| **Figma** | Prototipat visual de la interfície mòbil i definició de l'estètica modern-medieval |

---

## 🎮 Funcionalitats principals

- **3 nivells de dificultat** — Fàcil (100pts), Intermèdia (200pts) i Difícil (350pts) amb taulers de mida creixent
- **Cronòmetre i bonus per rapidesa** — Com menys temps, més puntuació extra
- **⚠️ L'Ampliació Maleïda** — Mecànica de risc pròpia: supera el tauler i decideix si arrisques la puntuació per ×2, ×4 o ×8... o ho perds tot
- **Rànquing global** — Dues classificacions: millor puntuació per partida i puntuació total acumulada
- **Sense registre** — El nom del jugador és l'identificador únic, sense contrasenyes

---

## 🗃️ Base de dades

El sistema de persistència es gestiona amb una base de dades relacional de 3 taules:

```sql
-- Exemple: consulta del Top 10 per millor puntuació
SELECT u.nom_jugador, MAX(p.puntuacio_obtinguda) AS millor_puntuacio
FROM partides p
JOIN usuaris u ON p.id_usuari = u.id_usuari
WHERE p.resultat = 'victòria'
GROUP BY u.nom_jugador
ORDER BY millor_puntuacio DESC
LIMIT 10;
```

**Taules:** `usuaris` · `nivells` · `partides`  
**Relacions:** Una partida pertany a un usuari i a un nivell (claus foranes)

---

## 👤 La meva contribució

El meu rol dins del projecte ha estat triple:

**🎨 Disseny del joc**  
Creació de les mecàniques principals del joc, inclosa la ideació i definició de l'Ampliació Maleïda, el sistema de multiplicadors de risc i l'equilibri de puntuació entre nivells.

**🗄️ Base de dades**  
Disseny complet del model relacional: definició de les taules, claus primàries i foranes, i creació de les consultes SQL per al rànquing global (millor partida i puntuació acumulada).

**📱 Interfície i UX/UI**  
Responsable de tot el disseny visual: prototipat a Figma, definició de l'estètica modern-medieval, adaptació a pantalles tàctils i implementació de la interfície final en HTML/CSS.

---

## 🧩 Problemes trobats i solucions

**Problema:** Definir el comportament del sistema de puntuació quan el jugador perd en una Ampliació Maleïda encadenada.  
**Solució:** Establir que qualsevol derrota durant una ampliació retorna 0 punts totals de la partida, independentment de les ampliacions superades prèviament. Això simplifica la lògica i augmenta la tensió del joc.

**Problema:** Dissenyar una base de dades que suportés tant el rànquing per millor partida com la puntuació total acumulada sense duplicar dades.  
**Solució:** Separar les responsabilitats en dues taules: `partides` guarda cada resultat individual, i `usuaris` acumula els `punts_totals`. Dues consultes SQL independents gestionen cadascuna de les classificacions.

---

## 📚 Què he après

- Com dissenyar un **model relacional complet** des de zero, identificant entitats, atributs i relacions
- La importància del **disseny centrat en l'usuari (UX)** abans d'implementar: prototipat a Figma primer, codi després
- Com **documentar un projecte de forma professional** per a que qualsevol persona pugui entendre'l en pocs minuts
- Gestió del codi amb **Git i GitHub** com a eina de treball real, no només d'emmagatzematge
- La diferència entre construir quelcom que *funciona* i construir quelcom que és *jugable i coherent*

---

## 🚀 Estat del projecte

> 🟡 **En desenvolupament** — Fase de disseny i base de dades completada. Implementació en curs.

| Fase | Estat |
|---|---|
| Disseny del joc i mecàniques | ✅ Completat |
| Model de base de dades | ✅ Completat |
| Prototip visual (Figma) | ✅ Completat |
| Implementació HTML/CSS/JS | 🔄 En curs |
| Integració amb la BD | ⏳ Pendent |

---

## 👨‍💻 Autor

**oojuelg2526-cmyk**  
Estudiant de DAW · Politècnics Barcelona · Curs 2025/2026  

[![GitHub](https://img.shields.io/badge/GitHub-oojuelg2526--cmyk-181717?style=flat&logo=github)](https://github.com/oojuelg2526-cmyk)
