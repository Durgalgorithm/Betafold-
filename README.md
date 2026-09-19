# 🧬 Betafold — Protein Secondary Structure Prediction, 3D Molecular Simulation & Clinical Mutation Pathology Platform

[![Live Demo](https://img.shields.io/badge/Live_Demo-Access_Betafold_Platform-blue?style=for-the-badge&logo=google-chrome)](https://ais-pre-yognod7qxmimkzvksjdk4q-304205435735.asia-east1.run.app)


### 🌐 Live Application Link for Recruiters & Researchers
> **Direct Live URL:** [https://ais-pre-yognod7qxmimkzvksjdk4q-304205435735.asia-east1.run.app](https://ais-pre-yognod7qxmimkzvksjdk4q-304205435735.asia-east1.run.app)  
> *Click above to explore the running platform directly in your browser without local installation.*

---

## 🔭 Vision & Objective

The central dogma of structural biology dictates that a protein's primary amino acid sequence encodes its three-dimensional folding pathway, governing its physiological function and therapeutic targetability. Traditional experimental methods like X-ray crystallography, cryo-electron microscopy, and NMR spectroscopy require months of specialized labor.

**Betafold** was engineered to solve this computational bottleneck by providing an end-to-end, browser-native biocomputational workbench. The platform enables structural biologists, geneticists, and students to:
1. **Predict Secondary Conformations Instantly**: Map linear polypeptide sequences into 3-state ($Q_3$: $\alpha$-Helix, $\beta$-Sheet, Random Coil) and 8-state ($Q_8$) secondary structures using biophysical statistical mechanics.
2. **Benchmark Against Ground Truth**: Compare predicted geometries directly against experimentally verified crystallographic coordinates from the **RCSB Protein Data Bank (PDB)** in real time.
3. **Bridge Folding to Clinical Genetics**: Decode how point mutations, charge inversions, and helix-breaking substitutions dismantle secondary structure and trigger pathogenic human diseases.
4. **Accelerate Computational Screening**: Perform on-demand drug discovery pocket analysis and structural stability assays with zero configuration.

---

## ✨ Core Features & Architectural Modules

### 1. 🔬 Biophysical Secondary Structure Prediction Engine
- **Multi-Factor Algorithmic Scoring**:
  - **Conformational Propensities**: Implements Chou-Fasman and GOR positional matrix weights for $\alpha$-helices, $\beta$-strands, and turns.
  - **Evolutionary PSSM Weighting**: Simulates conservation profiles to reward residue stability across biological homologs.
  - **Hydropathy Analysis**: Kyte-Doolittle hydrophobicity index evaluation to accurately identify buried cores versus exposed solvent-accessible loops.
  - **Solvent Accessibility Modeling**: Classifies each residue into `Buried`, `Intermediate`, or `Exposed`.
- **Rigorous Quantitative Metrics**:
  - **$Q_3$ Metric Accuracy (%)**: Residue-by-residue correspondence between prediction and experimental DSSP ground truth.
  - **Segment Overlap Measure ($SOV$)**: Standardized structural biology metric evaluating continuous secondary structural segments rather than isolated point predictions.

### 2. 🧪 Dual-Engine 3D Interactive Molecular Visualizer
- **Hardware-Accelerated WebGL Rendering**:
  - Powered by **3Dmol.js** with an integrated fallback to **Three.js**, guaranteeing fluid 60 FPS molecular inspection across all devices.
  - Interactive camera controls: Full 3D rotation, smooth zoom, pan, and reset.
- **Dual Visual Modes**:
  - **Side-by-Side Split View**: Independent or synchronized dual-viewport comparing predicted structural topology against experimental PDB structures.
  - **Superimposed Alignment View**: Overlay predicted topology directly with experimental crystallographic backbones.
- **Coloring Archetypes**:
  - Color by **Secondary Structure** ($\alpha$-Helix in red/purple, $\beta$-Sheet in cyan/yellow, Coil in slate).
  - Color by **B-Factor / Prediction Confidence**.
  - Color by **Residue Hydropathy / Polarity**.

### 3. 🧬 Clinical Mutation Pathology & *In Silico* Mutagenesis
- **Comprehensive Biological Knowledge Base**:
  - Detailed normal physiological summaries, biological pathways, and subcellular localization for protein targets.
- **Mutation-Induced Disease Phenotyping**:
  - Clinically grounded documentation of human diseases (e.g., Alpha-Thalassemia, early-onset neurodegenerative tauopathies, infant Triosephosphate Isomerase deficiency, hemolytic anemia).
  - Categorization by clinical severity (**Severe**, **Moderate**, **Mild**).
- **Interactive Biophysical Mutagenesis Assay**:
  - **Helix Breaker ($Xaa \to Pro$)**: Visualizes disruption of the $i \to i+4$ backbone hydrogen bond and steric clash from pyrrolidine ring ($\Delta\Delta G \approx +3.8\text{ kcal/mol}$).
  - **Buried Charge Inversion**: Evaluates desolvation penalties and catastrophic core repulsion ($\Delta\Delta G \approx +4.5\text{ kcal/mol}$).
  - **Core Cavity Creation ($Leu/Ile \to Ala$)**: Evaluates vacuum cavity formation and loss of Van der Waals packing ($\Delta\Delta G \approx +2.1\text{ kcal/mol}$).
  - **Disulfide Bridge Deletion ($Cys \to Ser/Ala$)**: Quantifies thermal destabilization ($T_m$ drop) and amyloid aggregation vulnerability ($\Delta\Delta G \approx +5.2\text{ kcal/mol}$).

### 4. 🤖 Gemini Molecular Reasoning Engine
- Server-side integration with Google's Gemini models for on-demand biochemical analysis:
  - Pocket druggability and cryptic binding site detection.
  - Secondary structure fold classification (TIM barrels, Globin folds, Greek key motifs).
  - Allosteric regulation assessment.

---

## 🏛️ System Architecture

```
┌────────────────────────────────────────────────────────────────────────┐
│                          Betafold Client (React 19)                    │
│                                                                        │
│  ┌───────────────────────┐  ┌────────────────────┐  ┌───────────────┐  │
│  │ 3Dmol.js / Three.js   │  │ Sequence & Metric  │  │ In Silico     │  │
│  │ Dual Molecular Viewer │  │ Tracks (Q3 / SOV)  │  │ Mutagenesis   │  │
│  └───────────▲───────────┘  └─────────▲──────────┘  └───────▲───────┘  │
│              │                        │                     │          │
│  ┌───────────┴────────────────────────┴─────────────────────┴───────┐  │
│  │               Bioinformatics & Biophysics Engine                 │  │
│  └────────────────────────────────────▲─────────────────────────────┘  │
└───────────────────────────────────────┼────────────────────────────────┘
                                        │
                                        ▼
┌────────────────────────────────────────────────────────────────────────┐
│                    Express Backend Service (Node.js / tsx)             │
│                                                                        │
│   • /api/protein-knowledge  ───►  Gemini 3.8 Flash Biological Reasoning│
│   • /api/pdb/:id            ───►  RCSB Protein Data Bank Proxy & Cache │
│   • /api/structure-insight  ───►  Cryptic Pocket Structural Analysis   │
└────────────────────────────────────────────────────────────────────────┘
```

---

## 🗂️ Curated Benchmark Library Included

Betafold includes pre-loaded, experimentally validated benchmark structures:

| PDB ID | Protein Name | Organism | Structural Class | Clinical Relevance |
| :--- | :--- | :--- | :--- | :--- |
| **1HBA** | Human Deoxyhemoglobin $\alpha$-chain | *Homo sapiens* | All $\alpha$-helical (Globin fold) | Alpha-Thalassemia, Hemolytic Anemias |
| **1UBQ** | Ubiquitin | *Homo sapiens* | Mixed $\alpha/\beta$ (Ubiquitin roll) | Proteasomal clearance, Neurodegeneration |
| **1CRN** | Crambin | *Crambe hispanica* | Plant thionin ($\alpha+\beta$) | Membrane lysis, Plant pathogen defense |
| **2TRX** | Thioredoxin | *Escherichia coli* | $\alpha/\beta$ sandwich | Cellular redox regulation, Oxidative stress |
| **1TIM** | Triosephosphate Isomerase | *Saccharomyces cerevisiae* | Canonical $(\beta/\alpha)_8$ TIM barrel | Glycolytic enzymopathy, Hemolytic crises |
| **1ENH** | Engrailed Homeodomain | *Drosophila melanogaster* | Helix-turn-helix transcription factor | Morphogenesis, Developmental patterning |

---

## 💻 Local Development Setup

### Prerequisites
- **Node.js**: v18+ or v20+
- **npm** or **yarn**

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/betafold.git
cd betafold
```

### 2. Install Dependencies
```bash
npm install
```

### 3. Configure Environment Variables
Create a `.env` file in the root directory (based on `.env.example`):
```env
GEMINI_API_KEY=your_gemini_api_key_here
```

### 4. Launch Development Server
```bash
npm run dev
```
The server will start at `http://localhost:3000`.

### 5. Build for Production
```bash
npm run build
npm start
```

---

## 🔒 Security & Data Integrity

- **Encrypted Transmission**: All PDB coordinate queries use HTTPS/TLS.
- **Client-Side Privacy**: Sequence predictions and mutation simulations execute entirely in-browser without sending user protein sequences to external databases.
- **Server-Side API Key Protection**: Gemini API keys are maintained exclusively within server-side execution scopes and are never leaked to client-side bundles.

---

## 👥 Authors & Acknowledgments
- Developed with **Google AI Studio** and **Gemini**.
- Benchmark coordinates provided by the **RCSB Protein Data Bank**.
- Biophysical rendering enabled by **3Dmol.js**.
