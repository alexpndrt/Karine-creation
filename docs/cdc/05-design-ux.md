# 05 - Design UX/UI

## Philosophie de design

### Valeurs transmises

- **Artisanal** : Authenticité, savoir-faire, tradition
- **Élégant** : Sobriété, raffinement, qualité
- **Accessible** : Simplicité, clarté, proximité
- **Professionnel** : Crédibilité, sérieux, confiance

### Palette couleur (inspirée couture)

```
Primaire : #8B4513 (Marron chocolat - élégance)
Secondaire : #D4AF37 (Or antique - prestige)
Accent : #2C5530 (Vert forêt - nature/tradition)
Neutre : #F5F5DC (Beige - toile de lin)
Texte : #2C2C2C (Anthracite)
```

### Typographie

- **Titres** : Playfair Display (serif élégant)
- **Corps** : Open Sans (sans-serif lisible)
- **Tailles** : Responsive scale (1.125, 1.25, 1.5, 2, 3rem)

---

## Architecture de l'information

### Structure mentale utilisateur

```
Je découvre → Je m'intéresse → Je contacte
    ↓            ↓              ↓
Accueil    Portfolio        Contact
Services   À propos        Tarifs
```

### Hiérarchie visuelle

1. **Hero** : Impact immédiat (titre + CTA)
2. **Navigation** : Accès rapide aux sections
3. **Contenu** : Informations organisées logiquement
4. **Preuve sociale** : Témoignages, portfolio
5. **Contact** : Conversion finale

---

## Wireframes principaux

### Page d'accueil (Mobile-first)

```
[Header - Logo + Menu burger]

[Hero Section - Full width]
┌─────────────────────────────────┐
│  🧵 KARINE CREATION            │
│  Couture sur mesure & retouches │
│  [CTA: Voir mes créations]     │
└─────────────────────────────────┘

[Services - 3 colonnes]
┌─────────┬─────────┬─────────┐
│ Robes   │Costumes │Retouches│
│ sur     │sur      │&        │
│ mesure  │mesure   │réparat. │
└─────────┴─────────┴─────────┘

[Portfolio - Carousel]
┌─────────────────────────────────┐
│ ◄ [Photo] [Photo] [Photo] ►    │
│   Légende courte               │
└─────────────────────────────────┘

[Témoignages - Citations]
┌─────────────────────────────────┐
│ "Travail impeccable..."        │
│ - Marie D., cliente            │
└─────────────────────────────────┘

[Footer - Contact rapide]
┌─────────────────────────────────┐
│ 📞 06.XX.XX.XX.XX              │
│ 📧 contact@karine-creation.fr  │
│ 📍 [Ville]                     │
└─────────────────────────────────┘
```

### Page Portfolio (Grille filtrable)

```
[Header + Filtres]
┌─────────────────────────────────┐
│ Filtres: [Tous] Robes Costumes │
└─────────────────────────────────┘

[Grille responsive]
┌─────┬─────┬─────┬─────┐
│Photo│Photo│Photo│Photo│
│     │     │     │     │
│Titre│Titre│Titre│Titre│
└─────┴─────┴─────┴─────┘

[Lightbox au clic]
┌─────────────────┐
│        ▲        │
│   [Photo large] │
│        ▼        │
│ ◄ Précédent Suivant ► │
│ Description détaillée  │
└─────────────────┘
```

---

## Composants UI

### Boutons (3 variantes)

- **Primaire** : CTA principal (fond marron, texte blanc)
- **Secondaire** : Actions secondaires (bordure marron)
- **Tertiaire** : Liens discrets (souligné)

### Cartes (Portfolio/Services)

- **Ombre douce** : Profondeur élégante
- **Ratio 4:3** : Harmonieux pour photos
- **Hover** : Légère élévation + zoom subtil

### Formulaires

- **Labels flottants** : UX moderne
- **États** : Normal, focus, error, success
- **Validation** : Temps réel avec messages clairs

### Navigation

- **Desktop** : Menu horizontal centré
- **Mobile** : Menu burger animé
- **États** : Normal, hover, active (couleur accent)

---

## Responsive Design

### Breakpoints stratégiques

- **Mobile** : 320px - 767px (portrait d'abord)
- **Tablet** : 768px - 1023px (landscape)
- **Desktop** : 1024px+ (grandes écrans)

### Adaptation par composant

#### Grille portfolio

- **Mobile** : 1 colonne (pleine largeur)
- **Tablet** : 2 colonnes
- **Desktop** : 3-4 colonnes

#### Hero

- **Mobile** : Texte centré, CTA full-width
- **Desktop** : Layout asymétrique, CTA à droite

#### Navigation

- **Mobile** : Menu burger + overlay
- **Desktop** : Menu horizontal + dropdowns

---

## Accessibilité intégrée

### Couleurs et contrastes

- **Texte principal** : Noir sur blanc (21:1)
- **Texte secondaire** : Gris foncé (12:1)
- **Liens** : Bleu accessible (4.5:1 minimum)

### Navigation clavier

- **Focus visible** : Outline bleu épais
- **Tab order** : Logique séquentiel
- **Skip links** : Accès rapide au contenu

### Lecteurs d'écran

- **Labels explicites** : Descriptions complètes
- **Structure sémantique** : Headings hiérarchisés
- **Alt texts** : Descriptions fonctionnelles

---

## Performance visuelle

### Animations (subtiles)

- **Hover** : Transitions 0.3s ease
- **Scroll** : Reveal progressif (lazy loading)
- **Loading** : Skeletons pour contenu dynamique

### Images optimisées

- **Format** : WebP avec fallback
- **Tailles** : Srcset responsive
- **Compression** : Qualité 80-90%

### Typographie web

- **Fallbacks** : Serif → sans-serif → monospace
- **Métriques** : Line-height 1.5, letter-spacing optimisé
- **Responsive** : Fluid typography (clamp())

---

## Outils et ressources

### Design system

- **Figma** : Maquettes interactives
- **Storybook** : Bibliothèque composants
- **Design tokens** : Variables centralisées

### Guidelines

- **Spacing scale** : 4px, 8px, 16px, 24px, 32px...
- **Border radius** : 4px, 8px, 12px, 24px
- **Shadows** : 3 niveaux (subtle, medium, strong)

### Tests utilisateurs

- **Prototype** : Version clickable pour validation
- **A/B tests** : Comparaison variantes CTA
- **Heatmaps** : Analyse comportement réel
