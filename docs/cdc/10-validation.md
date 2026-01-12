# 10 - Critères de Validation et Tests

## Méthodologie de validation

### Approche qualité

#### Tests en pyramide

```
UI Tests (E2E)     ████░░░░ 20%
Integration Tests  ████████ 40%
Unit Tests         ██████████ 40%
```

#### Niveaux validation

- **Fonctionnel** : Features opérationnelles
- **Technique** : Performance, sécurité, accessibilité
- **Utilisateur** : UX, design, contenu
- **Business** : Conversion, ROI, satisfaction

---

## Critères d'acceptation détaillés

### CA001 - Site accessible et navigable

**Étant donné** un utilisateur avec connexion internet
**Quand** il accède à karine-creation.fr
**Alors** le site se charge en < 3 secondes
**Et** la navigation est fluide sur mobile/desktop

**Critères techniques** :

- [ ] Temps chargement < 3s (Lighthouse)
- [ ] Responsive : breakpoints 320px, 768px, 1024px
- [ ] HTTPS obligatoire
- [ ] Erreur 404 personnalisée

### CA002 - Portfolio fonctionnel

**Étant donné** un visiteur intéressé par les créations
**Quand** il consulte la page portfolio
**Alors** il peut filtrer par catégorie (robes, costumes, retouches)
**Et** visualiser les photos en haute qualité

**Critères techniques** :

- [ ] Grille responsive (1-4 colonnes)
- [ ] Filtres actifs (boutons + dropdown)
- [ ] Lightbox avec navigation
- [ ] Images optimisées WebP
- [ ] Métadonnées (matières, techniques)

### CA003 - Formulaire contact opérationnel

**Étant donné** un prospect souhaitant contacter
**Quand** il remplit le formulaire
**Alors** il reçoit confirmation immédiate
**Et** Karine reçoit l'email dans l'heure

**Critères techniques** :

- [ ] Validation temps réel (email, champs requis)
- [ ] Protection anti-spam (honeypot)
- [ ] Email confirmation utilisateur
- [ ] Email réception professionnelle
- [ ] Stockage RGPD compliant

### CA004 - SEO optimisé

**Étant donné** une recherche "couture [ville]"
**Quand** un utilisateur recherche sur Google
**Alors** le site apparaît en première page
**Et** la meta description est accrocheuse

**Critères techniques** :

- [ ] Title optimisé (< 60 caractères)
- [ ] Meta description (< 160 caractères)
- [ ] Core Web Vitals > 75/100
- [ ] Sitemap.xml généré
- [ ] Schema.org LocalBusiness

### CA005 - Accessibilité RGAA AA

**Étant donné** un utilisateur en situation handicap
**Quand** il navigue sur le site
**Alors** il peut accéder à tout le contenu
**Et** utiliser toutes les fonctionnalités

**Critères techniques** :

- [ ] Navigation clavier complète
- [ ] Lecteurs d'écran compatibles
- [ ] Contraste couleurs > 4.5:1
- [ ] Focus visible et logique
- [ ] Langue déclarée (fr-FR)

---

## Plan de tests

### Tests unitaires (Unit Tests)

#### Composants React

```typescript
// Exemple test bouton
describe("Button", () => {
  it("renders with correct text", () => {
    render(<Button>Click me</Button>);
    expect(screen.getByText("Click me")).toBeInTheDocument();
  });

  it("calls onClick when clicked", () => {
    const handleClick = jest.fn();
    render(<Button onClick={handleClick}>Click me</Button>);
    fireEvent.click(screen.getByText("Click me"));
    expect(handleClick).toHaveBeenCalledTimes(1);
  });
});
```

#### Utilitaires

- **Validation email** : Formats valides/invalides
- **Formatage prix** : Devises, séparateurs
- **Calcul dimensions** : Tailles responsive
- **API calls** : Mock responses

**Couverture cible** : > 80%

### Tests d'intégration (Integration Tests)

#### API Routes

- **Contact form** : Soumission → email → confirmation
- **Portfolio filters** : Sélection → résultats filtrés
- **Navigation** : Routing Next.js fonctionnel

#### Composants complexes

- **Gallery** : Chargement images + filtres
- **Forms** : Validation + soumission + feedback
- **Layout** : Responsive + navigation

### Tests end-to-end (E2E)

#### Scénarios utilisateurs

```typescript
// Exemple Playwright
test("complete user journey", async ({ page }) => {
  // Accès accueil
  await page.goto("http://localhost:3000");
  await expect(page).toHaveTitle(/Karine Creation/);

  // Navigation portfolio
  await page.click("text=Portfolio");
  await expect(page).toHaveURL(/.*portfolio/);

  // Filtrage créations
  await page.click("text=Robes");
  await expect(page.locator(".gallery-item")).toHaveCount(5);

  // Contact
  await page.click("text=Contact");
  await page.fill("[name=email]", "test@example.com");
  await page.fill("[name=message]", "Demande devis");
  await page.click("button[type=submit]");
  await expect(page).toHaveText("Message envoyé");
});
```

#### Parcours critiques

- **Premier visiteur** : Découverte → intérêt → contact
- **Mobile user** : Navigation tactile fluide
- **SEO crawler** : Structure accessible robots

---

## Validation non-fonctionnelle

### Performance

- **Lighthouse** : Score > 90/100 toutes catégories
- **WebPageTest** : Start Render < 1.5s
- **Core Web Vitals** : Tous verts (good)
- **Bundle size** : < 200KB gzippé

### Sécurité

- **OWASP Top 10** : Audit passé
- **Headers** : CSP, HSTS, X-Frame-Options
- **Dependencies** : Audit npm clean
- **SSL** : A+ rating SSL Labs

### Accessibilité

- **RGAA** : Niveau AA validé
- **WCAG** : Conformité 2.1 AA
- **Outils** : WAVE, axe, Lighthouse
- **Tests utilisateurs** : 3 personnes handicapées

### Compatibilité

- **Navigateurs** : Chrome, Firefox, Safari, Edge
- **Versions** : Support 2 dernières versions
- **Mobile** : iOS Safari, Chrome Android
- **Écrans** : 320px à 2560px+

---

## Outils et environnement de test

### Environnement local

```bash
# Setup test environment
npm run dev        # Development server
npm run build      # Production build
npm run test       # Unit tests
npm run test:e2e   # E2E tests
npm run lint       # Code quality
```

### Outils automatisés

- **Jest** : Tests unitaires
- **React Testing Library** : Tests composants
- **Playwright** : Tests E2E
- **Cypress** : Alternative E2E
- **Lighthouse CI** : Performance

### Monitoring production

- **Sentry** : Erreurs et performance
- **Google Analytics** : Comportement utilisateurs
- **Google Search Console** : SEO et indexation
- **Uptime Robot** : Disponibilité

---

## Processus de validation

### Revue de code (Code Review)

- **Pull Request** : Template checklist
- **Standards** : ESLint, Prettier respectés
- **Tests** : Couverture maintenue
- **Performance** : Bundle size contrôlé
- **Sécurité** : Audit automatique

### Validation client

- **Démonstration** : Fonctionnalités clés
- **Tests utilisateurs** : Feedback recueilli
- **Corrections** : Itérations si nécessaire
- **Approbation** : Go/no-go final

### Déploiement

- **Environnement staging** : Tests pré-production
- **Smoke tests** : Fonctionnalités critiques
- **Rollback plan** : Procédure retour arrière
- **Monitoring** : Alertes post-déploiement

---

## Métriques qualité

### Code quality

- **Coverage** : > 80% statements, branches, functions
- **Complexity** : Functions < 20 lines
- **Duplication** : < 5% code dupliqué
- **Maintainability** : Grade A (CodeClimate)

### Performance

- **First Paint** : < 1.5 secondes
- **Speed Index** : < 3 secondes
- **Time to Interactive** : < 3.5 secondes
- **Bundle size** : < 200KB

### Utilisateur

- **Task completion** : > 90% scénarios réussis
- **Error rate** : < 5% actions échouées
- **Satisfaction** : SUS score > 70
- **Accessibility** : 0 erreur critique

---

## Gestion des anomalies

### Classification

- **Critique** : Bloque fonctionnalité majeure
- **Majeure** : Impact fort utilisateur
- **Mineure** : Impact limité
- **Cosmétique** : Problème esthétique

### Processus résolution

1. **Détection** : Tests automatisés ou manuels
2. **Priorisation** : Impact × fréquence
3. **Correction** : Développement + tests
4. **Validation** : Tests régression
5. **Déploiement** : Release avec suivi

### Suivi qualité

- **Tableau bord** : Métriques temps réel
- **Rapports hebdomadaires** : Tendances
- **Alertes** : Seuils dépassés
- **Amélioration** : Actions correctives

---

## Checklist finale lancement

### Fonctionnel

- [ ] Toutes user stories validées
- [ ] Formulaire contact testé
- [ ] Portfolio navigable
- [ ] Pages responsive

### Technique

- [ ] Performance > 90/100
- [ ] Accessibilité RGAA AA
- [ ] SEO optimisé
- [ ] Sécurité auditée

### Contenu

- [ ] Textes validés orthographe
- [ ] Images optimisées
- [ ] Coordonnées à jour
- [ ] Mentions légales

### Production

- [ ] Domaine configuré
- [ ] SSL actif
- [ ] Monitoring opérationnel
- [ ] Backup fonctionnel

### Communication

- [ ] Réseaux sociaux créés
- [ ] Email professionnel
- [ ] Site référencé Google
- [ ] Contacts fournisseurs

---

## Maintenance qualité

### Tests continus

- **CI/CD** : Tests automatisés à chaque push
- **Monitoring** : Alertes performance
- **Audits** : Sécurité trimestriels
- **Mises à jour** : Dépendances suivies

### Amélioration continue

- **Feedback utilisateurs** : Recueillis et analysés
- **Analytics** : Comportement mesuré
- **A/B tests** : Optimisations itératives
- **Benchmarks** : Comparaison concurrents

Cette approche qualité garantit un produit professionnel, maintenable et évolutif !
