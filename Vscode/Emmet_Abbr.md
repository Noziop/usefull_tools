# Emmet Cheatsheet - Table des Matières 📚

## I. Fondamentaux Emmet 🛠
- [Astuces Pro & Raccourcis](#astuces-pro)
- [Structure de Base](#structure-de-base)
- [Opérateurs & Groupement](#opérateurs--groupement)
- [Sélecteurs & Classes](#sélecteurs--classes)

## II. Composants de Base 📦
- [Éléments HTML](#éléments-html)
- [Média & Métadonnées](#média--métadonnées)
- [Snippets Utilitaires](#snippets-utilitaires)

## III. Navigation & Layout 🗺
- [Navigation](#navigation)
- [Structures Sémantiques](#structures-sémantiques)
- [Mega Menu](#mega-menu)

## IV. Formulaires & Inputs 📝
- [Formulaires Basiques](#formulaires-basiques)
- [Formulaires Avancés](#formulaires-avancés)
- [Input Fields Animés](#input-fields-animés)
- [Validation Forms](#validation-forms)

## V. Composants UI 🎨
- [Composants Complexes](#composants-complexes)
- [UI Moderne](#ui-moderne)
- [Interface Avancée](#interface-avancée)
- [Accessibilité](#accessibilité)

## VI. Structures de Données 📊
- [Structures Dynamiques](#structures-dynamiques)
- [Tables de Données](#tables-de-données)
- [Grilles de Cards](#grilles-de-cards)

## VII. Marketing & Landing Pages 🚀
- [Sections Marketing](#sections-marketing)
- [Hero Sections](#hero-sections)
- [Features](#features)
- [Pricing](#pricing)

## VIII. Micro-Interactions & Animations ✨
- [Interactions Magiques](#interactions-magiques)
- [Effets Subtils](#effets-subtils)
- [Feedback Animations](#feedback-animations)

## IX. Composants Applicatifs 💻
- [Web App](#web-app)
- [Dashboard](#dashboard)
- [Notifications](#notifications)
- [Contrôles UI](#contrôles-ui)

## X. Conclutsion - Salut à toi, Emmet Warrior ! 🤘
- [Pour les Warrior.e.s du Code](#pour-les-warriores-du-code)
- [Points Clés à Retenir](#points-cles-a-retenir)
- [Pour Aller Plus Loin](#pour-aller-plus-loin)

# Emmet Cheatsheet

## I. Fondamentaux Emmet 🛠

### Astuces Pro
```html
# Raccourcis Essentiels
TAB           → Déclenche l'expansion Emmet
Ctrl + Space  → Affiche les suggestions
>             → Enfant (parent>enfant)
+             → Frère (element+element)
^             → Remonter d'un niveau
*             → Multiplicateur
$             → Numérotation automatique
{}            → Ajout de texte
[]            → Attributs personnalisés
```

### Structure de Base
```html
# Templates HTML
!             → Template HTML5 complet
html:5        → Même chose que !
doc           → Document HTML basique

# Structure Simple
html[lang=fr] → <html lang="fr"></html>
meta:vp       → Viewport meta tag
link:css      → Lien stylesheet CSS
script:src    → Script avec src externe
```

### Opérateurs & Groupement
```html
# Opérateurs de Base
div>p         → <div><p></p></div>
div+p         → <div></div><p></p>
div>p^span    → <div><p></p></span>
(div>p)*2     → <div><p></p></div><div><p></p></div>

# Groupement Avancé
(header>nav>ul>li*3)+footer
→ Crée header avec nav, liste de 3 items, et footer séparé
```

### Sélecteurs & Classes
```html
# ID et Classes
div#header    → <div id="header"></div>
div.container → <div class="container"></div>
div.c1.c2     → <div class="c1 c2"></div>

# Multiplicateurs avec Classes
div.item$*3   → Crée 3 divs avec classes item1, item2, item3
```

## II. Composants de Base 📦

### Éléments HTML
```html
# Texte
p             → <p></p>
h$*6          → <h1></h1> à <h6></h6>
p{texte}      → <p>texte</p>

# Listes
ul>li*5       → Liste non ordonnée avec 5 items
ol>li*3       → Liste ordonnée avec 3 items
dl>dt+dd      → Liste de définition
```

### Média & Métadonnées
```html
# Images et Média
img           → <img src="" alt="">
img:z         → <img src="" alt="" sizes="" srcset="">
video         → <video src=""></video>
audio         → <audio src=""></audio>

# Meta Tags
meta:utf      → Meta UTF-8
meta:desc     → Meta description
meta:og       → Open Graph meta
```

### Snippets Utilitaires
```html
# Lorem Ipsum
lorem         → Paragraphe lorem ipsum
lorem10       → 10 mots de lorem ipsum
lorem*3       → 3 paragraphes

# Commentaires
c             → <!-- -->
cc:ie         → Commentaire conditionnel IE
```

## III. Navigation & Layout 🗺

### Navigation
```html
# Navigation de Base
nav>ul>li*4>a    → Nav basique avec 4 liens
header>nav.main   → Header avec nav principale

# Navigation Avancée
nav.navbar>(ul.nav-list>li.nav-item*4>a.nav-link{Menu $})
→ Nav avec classes Bootstrap-style

# Breadcrumbs
nav.breadcrumb>ul>li.breadcrumb-item*3>a{Level $}
```

### Structures Sémantiques
```html
# Layout de Base
header+main+footer    → Structure basique
main>section*3        → Main avec 3 sections

# Article Complet
article>(header>h1+p.meta)+section.content+footer.article-footer

# Aside
aside.sidebar>section*3>h3+ul>li*4
```

### Mega Menu
```html
# Structure Mega Menu
nav.mega>(ul.main-menu>li.menu-item*4>a{Category $}+(div.dropdown>(div.col>h3+ul>li*4>a)*3))

# Dropdown Simple
li.dropdown>(a.dropdown-toggle+ul.dropdown-menu>li*4>a)
```

## IV. Formulaires & Inputs 📝

### Formulaires Basiques
```html
# Structure Simple
form>input:text+input:email+button:submit

# Labels et Inputs
form>(label+input:text)*3    → 3 paires label/input
form>(label[for=$]+input#$)*3    → Avec for et id

# Groupes de Champs
fieldset>legend{User Info}+(div.field>label+input)*3
```

### Formulaires Avancés
```html
# Validation
form.needs-validation>(div.form-group>label+input[required])*3

# Input Groups
div.input-group>input:text+div.input-group-append>button{Search}

# Checkbox & Radio
div.form-check>(input:checkbox#check$+label[for=check$])*3
```

### Input Fields Animés
```html
# Floating Labels
div.form-floating>input:text+label

# Input avec Icône
div.input-icon>(input:text+i.icon)

# Input avec Animation
div.input-wrapper>(input:text.animated+label.animated+.line)
```

### Validation Forms
```html
# Messages d'Erreur
div.form-group>(input:text+span.error-message)

# États de Validation
input:text[data-validate].success
input:text[data-validate].error

# Feedback Visuel
div.feedback-wrapper>(input+svg.check+svg.error)
```

## V. Composants UI 🎨

### Composants Complexes
```html
# Cards
div.card>(div.card-header>h3{Title})+div.card-body>p+a.btn{Read More}

# Modal
div.modal[aria-hidden="true"]>(div.modal-dialog>div.modal-content>(div.modal-header>h5+button.close)+div.modal-body+div.modal-footer)

# Accordéon
div.accordion>(div.accordion-item>h2>button.accordion-trigger+div.accordion-content)*3
```

### UI Moderne
```html
# Dark Mode Toggle
button.theme-toggle[aria-label="Toggle theme"]>(span.sun+span.moon)

# Toast Notifications
div.toast-container>div.toast[role="alert"]>(div.toast-header+div.toast-body)

# Search avec Autocomplete
div.search-wrapper>(input.search[type="search"]+div.suggestions>ul>li*5)
```

### Interface Avancée
```html
# Tabs
div.tabs[role="tablist"]>(button.tab*3)+div.tab-content>(div.tab-pane)*3

# Slider
div.slider>(div.slide*5)+button.prev+button.next

# Dropdown Complexe
div.dropdown>(button.dropdown-toggle+div.dropdown-menu>a.dropdown-item*4)
```

### Accessibilité
```html
# Navigation Skip Links
div.skip-links>a.skip-main[href="#main"]{Skip to main content}

# ARIA Labels
button[aria-label="Close"][aria-expanded="false"]

# Focus Management
div.focus-trap[tabindex="-1"]>div.dialog[role="dialog"]
```

## VI. Structures de Données 📊

### Structures Dynamiques
```html
# Liste de Données
ul.data-list>li.data-item*5>(h3{Item $}+p>lorem10)

# Grille Responsive
div.grid-container>(div.grid-item>h3{Title $}+p{Content $})*12

# Timeline
div.timeline>(div.timeline-item>(div.date{202$}+div.content>h3+p))*5
```

### Tables de Données
```html
# Table Basique
table.data-table>thead>tr>th*5{Header $}^^tbody>tr*3>td*5{Cell $}

# Table Responsive
div.table-responsive>table.table>(thead>tr>th*4)+(tbody>tr*5>td*4)

# Table avec Tri
table.sortable>(thead>tr>th[data-sort]*4)+(tbody>tr*3>td*4)
```

### Grilles de Cards
```html
# Grid Layout Moderne
div.cards-grid>(article.card>(img[src="img$.jpg"]+div.content>h3{Title $}+p+a.btn))*6

# Masonry Layout
div.masonry>(div.masonry-item>img+h3+p)*8

# Portfolio Grid
div.portfolio>(figure.portfolio-item>img+figcaption>h3+p)*9
```

## VII. Marketing & Landing Pages 🚀

### Sections Marketing
```html
# Hero Section
section.hero>(div.hero-content>h1.title{Welcome}+p.subtitle+a.cta-btn{Get Started})+div.hero-image>img

# Features Grid
section.features>div.container>(div.feature-card>i.icon+h3+p)*6

# Social Proof
section.testimonials>(div.testimonial>img.avatar+blockquote+cite)*3
```

### Hero Sections
```html
# Hero Minimaliste
section.hero-minimal>div.container>h1+p+button.cta

# Hero Split
section.hero-split>(div.left>h1+p+button)+(div.right>img)

# Hero Video
section.hero-video>(div.content>h1+p)+(video.bg-video[autoplay loop muted])
```

### Features
```html
# Feature List
ul.features-list>li.feature*6>(i.icon+h4+p)

# Feature Comparison
div.features-compare>(div.plan>h3{Basic}+ul>li*5)*3

# Feature Showcase
section.showcase>(article.feature-highlight>img+div.content>h3+p)*3
```

### Pricing
```html
# Pricing Cards
div.pricing-cards>(div.price-card>h3{Plan $}+.price{$9}+ul>li*5+a.btn{Choose})*3

# Pricing Table
table.pricing-table>tr>th*4^^(tr>td*4)*3

# Pricing Toggle
div.pricing-toggle>(button.monthly{Monthly}+label.switch+button.yearly{Yearly})
```

## VIII. Micro-Interactions & Animations ✨

### Interactions Magiques
```html
# Boutons Animés
button.magic-btn>(span.circle)+(span.text{Click Me})

# Curseur Custom
div.cursor-follow>(div.cursor)+(div.trail)*5

# Loading Animations
div.loader>(div.circle)*12
```

### Effets Subtils
```html
# Hover Effects
a.hover-effect>(span.text)+(span.line)

# Ripple Effect
button.ripple[data-ripple]>span.text{Click}

# Smooth Scroll
nav.smooth-scroll>a[href^="#"]*5
```

### Feedback Animations
```html
# Success/Error
div.feedback>(svg.success)+(svg.error)

# Progress Steps
div.progress-steps>(div.step>span.number{$})*4

# Form Validation
div.input-feedback>(input)+(svg.check)+(svg.cross)
```

## IX. Composants Applicatifs 💻

### Web App
```html
# App Shell
div.app-shell>(header.app-header>nav.app-nav)+(main.app-content)+(footer.app-footer)

# Side Panel
aside.side-panel[data-visible="false"]>(div.panel-header>h3+button.close)+div.panel-content

# App Settings
div.settings-panel>(div.settings-group>h4{Display}+div.options)*4
```

### Dashboard
```html
# Dashboard Layout
div.dashboard>(aside.sidebar>nav.dash-nav)+(main.dash-content>header.dash-header+div.widgets-grid)

# Widgets
div.widget-grid>(div.widget>div.widget-header+div.widget-body)*6

# Stats Cards
div.stats-container>(div.stat-card>h3.stat-title+p.stat-value+small.stat-change)*4
```

### Notifications
```html
# Notification Center
div.notif-center>(div.notif-header>h3+button.clear-all)+div.notif-list>div.notif-item*5

# Alert Types
div.alerts>(div.alert[role="alert"][type="$"]{Alert message})*4

# Toast Stack
div.toast-stack[aria-live="polite"]>(div.toast>div.toast-content+button.close)*3
```

### Contrôles UI
```html
# Data Controls
div.data-controls>(div.search-bar>input+button)+(div.filters>select*3)+(div.view-toggle>button*2)

# User Menu
div.user-menu>(img.avatar+span.username+div.dropdown>a*4)

# Action Bar
div.action-bar>(div.bulk-actions>button*3)+(div.pagination>button*5)
```

*Éclate de rire en mode rock'n'roll* 🎸

# Conclusion - Salut à toi, Emmet Warrior ! 🤘

Après cette épique aventure à travers les contrées du HTML, et des Emmet Abbreviation, voici ce qu'il faut retenir :

## Pour les Warrior.e.s du Code
- Tu as maintenant une boîte à outils complète d'abréviations Emmet
- De la base jusqu'aux composants les plus complexes
- Des micro-interactions qui en jettent
- Et tout dans la bonne humeur !

## Points Cles a Retenir
- Commence simple, deviens complexe
- La pratique fait la perfection
- Les raccourcis sont tes amis
- L'accessibilité n'est pas une option

## Pour Aller Plus Loin
- Personnalise tes snippets
- Crée tes propres abréviations
- Partage avec la communauté
- Et surtout, AMUSE-TOI !

*Petite dédicace punk-rock*  

*Chante doucement*  

"Salut à toi, ô codeur.euse jusqu'au-boutiste,  
Qui a traversé les plaines du code sans faiblir,  
Qui maîtrise maintenant Emmet comme un.e artiste,  
Et peut enfin coder sans avoir à souffrir !" 🎸

RESPECT ! 🤘✨