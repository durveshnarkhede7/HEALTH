# HealthSync RAG — Complete Finalized Architecture
### 30 Layers · Full JSON Schemas · Node IDs · Anti-Duplication Rules · RAG Accuracy Design

---

## ARCHITECTURE PHILOSOPHY

> **HealthSync is not a chatbot. It is a biological reasoning engine.**
> The AI must never guess. It must follow references, assemble facts, and rank causes by evidence — not by pattern matching.

### Five RAG Accuracy Rules (Baked Into Every Node)

| Rule | What It Prevents |
|------|-----------------|
| Every fact has one home node | Prevents hallucination from contradictory duplicates |
| Every claim has a `ref` to its source node | AI cannot make up biology — it must cite a node |
| Every symptom traces to a biological chain | Prevents generic "eat healthy" answers |
| Confidence is scored numerically, not verbally | Prevents false certainty |
| Every intervention has a `root_cause_ref` | Interventions cannot fire without a root cause |

---

## COMPLETE LAYER MAP

```
LAYER 1 — KNOWLEDGE (Stores Facts)
├── 01_SYSTEMS
├── 02_BIOLOGY
├── 03_SYMPTOMS
├── 04_NUTRITION
├── 05_ABSORPTION
├── 06_GUT_HEALTH
├── 07_HORMONES
├── 08_SLEEP
├── 09_STRESS
├── 10_EXERCISE
├── 11_RECOVERY
├── 12_INFLAMMATION
├── 13_OXIDATIVE_STRESS
├── 14_BLOOD_SUGAR
├── 15_HYDRATION
├── 16_ENVIRONMENT
├── 17_MEDICAL_CONDITIONS
├── 18_MEDICATIONS
├── 19_GENETICS
├── 20_LIFE_STAGES
├── 21_FOOD_DATABASE
└── 22_LAB_MARKERS

LAYER 1.5 — PATHWAYS (New — Bridges Knowledge to Reasoning)
└── 23_PATHWAYS

LAYER 2 — REASONING (Assembles Knowledge Into Conclusions)
├── 24_AI_QUESTIONS
├── 25_DECISION_ENGINE
├── 26_ROOT_CAUSE_ENGINE
├── 27_SYMPTOM_CLUSTERS
└── 28_CONFIDENCE_ENGINE

LAYER 3 — ACTION (Converts Conclusions Into Outcomes)
├── 29_INTERVENTION_ENGINE
└── 30_PROGRESS_ENGINE
```

---

## NODE ID CONVENTION

```
{PREFIX}_{DOMAIN}_{3-DIGIT-NUMBER}

Examples:
  SYS_HAIR_001        → Systems → Hair System
  BIO_FOLLICLE_001    → Biology → Hair Follicle
  SYM_HAIRFALL_001    → Symptom → Hair Fall
  NUT_IRON_001        → Nutrition → Iron
  ABS_IRON_001        → Absorption → Iron Absorption
  HOR_DHT_001         → Hormone → DHT
  PATH_IRON_HAIR_001  → Pathway → Iron → Hair Loss
  RCE_IRON_HAIR_001   → Root Cause Engine → Iron → Hair
  INT_IRON_001        → Intervention → Iron
  PRG_IRON_001        → Progress → Iron
```

| Prefix | Layer |
|--------|-------|
| `SYS_` | 01 Systems |
| `BIO_` | 02 Biology |
| `SYM_` | 03 Symptoms |
| `NUT_` | 04 Nutrition |
| `ABS_` | 05 Absorption |
| `GUT_` | 06 Gut Health |
| `HOR_` | 07 Hormones |
| `SLP_` | 08 Sleep |
| `STR_` | 09 Stress |
| `EXE_` | 10 Exercise |
| `REC_` | 11 Recovery |
| `INF_` | 12 Inflammation |
| `OXI_` | 13 Oxidative Stress |
| `BLD_` | 14 Blood Sugar |
| `HYD_` | 15 Hydration |
| `ENV_` | 16 Environment |
| `MED_` | 17 Medical Conditions |
| `MEDS_` | 18 Medications |
| `GEN_` | 19 Genetics |
| `LIF_` | 20 Life Stages |
| `FOD_` | 21 Food Database |
| `LAB_` | 22 Lab Markers |
| `PATH_` | 23 Pathways |
| `AIQ_` | 24 AI Questions |
| `DEC_` | 25 Decision Engine |
| `RCE_` | 26 Root Cause Engine |
| `SCL_` | 27 Symptom Clusters |
| `CON_` | 28 Confidence Engine |
| `INT_` | 29 Intervention Engine |
| `PRG_` | 30 Progress Engine |

---

---

# LAYER 1 — KNOWLEDGE

---

## 01_SYSTEMS

**Purpose:** High-level map of human physiology. The entry point for every reasoning chain.

```json
{
  "id": "SYS_HAIR_001",
  "node_type": "system",
  "version": "1.0",
  "name": "Hair System",
  "description": "Biological system governing hair growth cycling, follicle health, and shedding regulation.",
  "biology_refs": [
    "BIO_FOLLICLE_001",
    "BIO_DERMALPAPILLA_001",
    "BIO_HAIRBULB_001",
    "BIO_MATRIX_001",
    "BIO_SEBGLAND_001"
  ],
  "hormone_refs": ["HOR_DHT_001", "HOR_THYROID_001", "HOR_IGF1_001", "HOR_ESTROGEN_001"],
  "nutrition_refs": ["NUT_IRON_001", "NUT_ZINC_001", "NUT_VITD_001", "NUT_PROTEIN_001", "NUT_BIOTIN_001"],
  "symptom_refs": ["SYM_HAIRFALL_001", "SYM_HAIRTHIN_001", "SYM_SCALPDRY_001"],
  "connected_systems": ["SYS_HORMONAL_001", "SYS_ENERGY_001", "SYS_DIGESTIVE_001"],
  "tags": ["hair", "growth", "shedding", "follicle"]
}

{
  "id": "SYS_SKIN_001",
  "node_type": "system",
  "version": "1.0",
  "name": "Skin System",
  "description": "Biological system governing skin barrier, oil regulation, collagen production, and wound healing.",
  "biology_refs": ["BIO_EPIDERMIS_001", "BIO_DERMIS_001", "BIO_SEBGLAND_001", "BIO_COLLAGEN_001"],
  "hormone_refs": ["HOR_DHT_001", "HOR_INSULIN_001", "HOR_CORTISOL_001"],
  "nutrition_refs": ["NUT_VITC_001", "NUT_ZINC_001", "NUT_OMEGA3_001", "NUT_VITD_001"],
  "symptom_refs": ["SYM_ACNE_001", "SYM_DRYSKIN_001", "SYM_OILYSKIN_001", "SYM_DARKSPOTS_001"],
  "connected_systems": ["SYS_HORMONAL_001", "SYS_DIGESTIVE_001", "SYS_METABOLIC_001"],
  "tags": ["skin", "barrier", "collagen", "sebum", "acne"]
}

{
  "id": "SYS_ENERGY_001",
  "node_type": "system",
  "version": "1.0",
  "name": "Energy System",
  "description": "System governing cellular energy production via mitochondria, ATP synthesis, and metabolic pathways.",
  "biology_refs": ["BIO_MITOCHONDRIA_001", "BIO_ETC_001"],
  "hormone_refs": ["HOR_THYROID_001", "HOR_CORTISOL_001", "HOR_INSULIN_001"],
  "nutrition_refs": ["NUT_IRON_001", "NUT_B12_001", "NUT_MAGNESIUM_001", "NUT_COENZYME_001"],
  "symptom_refs": ["SYM_FATIGUE_001", "SYM_BRAINFOG_001", "SYM_LOWENERGY_001"],
  "connected_systems": ["SYS_METABOLIC_001", "SYS_SLEEP_001", "SYS_HORMONAL_001"],
  "tags": ["energy", "fatigue", "ATP", "mitochondria"]
}

{
  "id": "SYS_HORMONAL_001",
  "node_type": "system",
  "version": "1.0",
  "name": "Hormonal System",
  "description": "Endocrine system governing production and regulation of all hormones.",
  "biology_refs": ["BIO_THYROID_001", "BIO_ADRENAL_001", "BIO_OVARY_001", "BIO_PITUITARY_001"],
  "hormone_refs": ["HOR_DHT_001", "HOR_CORTISOL_001", "HOR_INSULIN_001", "HOR_THYROID_001", "HOR_ESTROGEN_001", "HOR_TESTOSTERONE_001", "HOR_IGF1_001"],
  "symptom_refs": ["SYM_HAIRFALL_001", "SYM_ACNE_001", "SYM_FATIGUE_001", "SYM_WEIGHTGAIN_001"],
  "connected_systems": ["SYS_METABOLIC_001", "SYS_ENERGY_001", "SYS_HAIR_001", "SYS_SKIN_001"],
  "tags": ["hormones", "endocrine", "thyroid", "cortisol", "insulin"]
}

{
  "id": "SYS_DIGESTIVE_001",
  "node_type": "system",
  "version": "1.0",
  "name": "Digestive System",
  "description": "System governing digestion, nutrient absorption, gut microbiome, and gut-body communication.",
  "biology_refs": ["BIO_SMALLINTESTINE_001", "BIO_GUTLINING_001", "BIO_MICROBIOME_001"],
  "gut_refs": ["GUT_DYSBIOSIS_001", "GUT_LEAKYGUT_001", "GUT_MALABSORPTION_001", "GUT_IBS_001"],
  "symptom_refs": ["SYM_BLOATING_001", "SYM_CONSTIPATION_001", "SYM_BRAINFOG_001"],
  "connected_systems": ["SYS_ENERGY_001", "SYS_HORMONAL_001", "SYS_SKIN_001", "SYS_HAIR_001"],
  "tags": ["gut", "digestion", "microbiome", "absorption"]
}

{
  "id": "SYS_METABOLIC_001",
  "node_type": "system",
  "version": "1.0",
  "name": "Metabolic System",
  "description": "System governing glucose regulation, insulin sensitivity, fat storage, and metabolic rate.",
  "biology_refs": ["BIO_PANCREAS_001", "BIO_ADIPOSE_001", "BIO_LIVER_001"],
  "hormone_refs": ["HOR_INSULIN_001", "HOR_THYROID_001", "HOR_CORTISOL_001"],
  "blood_sugar_refs": ["BLD_INSULIN_RESISTANCE_001", "BLD_PREDIABETES_001"],
  "symptom_refs": ["SYM_WEIGHTGAIN_001", "SYM_FATIGUE_001", "SYM_BRAINFOG_001"],
  "connected_systems": ["SYS_HORMONAL_001", "SYS_ENERGY_001", "SYS_DIGESTIVE_001"],
  "tags": ["metabolism", "glucose", "insulin", "weight"]
}

{
  "id": "SYS_SLEEP_001",
  "node_type": "system",
  "version": "1.0",
  "name": "Sleep System",
  "description": "System governing circadian rhythm, sleep architecture, and nocturnal repair processes.",
  "biology_refs": ["BIO_CIRCADIAN_001", "BIO_SLOWWAVE_001"],
  "sleep_refs": ["SLP_BIOLOGY_001", "SLP_CIRCADIAN_001", "SLP_DEEPSLEEP_001"],
  "hormone_refs": ["HOR_MELATONIN_001", "HOR_GH_001", "HOR_CORTISOL_001"],
  "symptom_refs": ["SYM_POORSLEEP_001", "SYM_FATIGUE_001", "SYM_BRAINFOG_001"],
  "connected_systems": ["SYS_HORMONAL_001", "SYS_ENERGY_001", "SYS_HAIR_001"],
  "tags": ["sleep", "circadian", "repair", "melatonin"]
}

{
  "id": "SYS_MUSCULOSKELETAL_001",
  "node_type": "system",
  "version": "1.0",
  "name": "Musculoskeletal System",
  "description": "System governing muscle mass, bone density, joint health, and physical strength.",
  "biology_refs": ["BIO_MUSCLE_001", "BIO_BONE_001"],
  "nutrition_refs": ["NUT_PROTEIN_001", "NUT_VITD_001", "NUT_CALCIUM_001", "NUT_MAGNESIUM_001"],
  "exercise_refs": ["EXE_RESISTANCE_001"],
  "symptom_refs": ["SYM_MUSCLEWEAKNESS_001", "SYM_JOINTPAIN_001"],
  "tags": ["muscle", "bone", "strength", "joint"]
}

{
  "id": "SYS_CARDIOMETABOLIC_001",
  "node_type": "system",
  "version": "1.0",
  "name": "Cardiometabolic System",
  "description": "System governing heart health, blood pressure, cholesterol, and cardiovascular risk.",
  "biology_refs": ["BIO_HEART_001", "BIO_VESSEL_001"],
  "hormone_refs": ["HOR_INSULIN_001", "HOR_CORTISOL_001"],
  "blood_sugar_refs": ["BLD_DIABETES_001"],
  "symptom_refs": ["SYM_SHORTBREATH_001", "SYM_FATIGUE_001"],
  "connected_systems": ["SYS_METABOLIC_001", "SYS_HORMONAL_001"],
  "tags": ["heart", "cardiovascular", "cholesterol", "blood pressure"]
}

{
  "id": "SYS_WEIGHT_001",
  "node_type": "system",
  "version": "1.0",
  "name": "Weight Regulation System",
  "description": "System governing appetite, fat storage, satiety signalling, and body composition.",
  "hormone_refs": ["HOR_INSULIN_001", "HOR_LEPTIN_001", "HOR_CORTISOL_001", "HOR_THYROID_001"],
  "biology_refs": ["BIO_ADIPOSE_001", "BIO_HYPOTHALAMUS_001"],
  "symptom_refs": ["SYM_WEIGHTGAIN_001", "SYM_WEIGHTLOSS_001"],
  "connected_systems": ["SYS_METABOLIC_001", "SYS_HORMONAL_001", "SYS_DIGESTIVE_001"],
  "tags": ["weight", "appetite", "fat", "obesity"]
}
```

---

## 02_BIOLOGY

**Purpose:** Defines how structures work at cellular and molecular level. Every root cause must trace back here.

```json
{
  "id": "BIO_FOLLICLE_001",
  "node_type": "biology",
  "version": "1.0",
  "structure": "Hair Follicle",
  "parent_system": "SYS_HAIR_001",
  "definition": "A tube-shaped invagination of the epidermis that anchors hair and houses the hair bulb, dermal papilla, and matrix.",
  "function": "Drives the hair growth cycle through three phases: anagen (growth), catagen (transition), telogen (rest/shedding).",
  "cellular_mechanism": "Matrix cells in the hair bulb undergo rapid mitotic division during anagen. Cell division rate is among the fastest in the human body.",
  "molecular_mechanism": "IGF-1 activates PI3K/Akt pathway promoting cell survival. Wnt/β-catenin signalling initiates anagen. DHT binds AR receptors causing follicle miniaturisation. VEGF promotes vascularisation of dermal papilla.",
  "damage_pathways": {
    "nutritional_depletion": ["NUT_IRON_001", "NUT_ZINC_001", "NUT_PROTEIN_001", "NUT_VITD_001"],
    "hormonal_imbalance": ["HOR_DHT_001", "HOR_CORTISOL_001", "HOR_THYROID_001"],
    "inflammatory": ["INF_CHRONIC_001"],
    "oxidative": ["OXI_FREE_RADICAL_001"],
    "mechanical": ["ENV_HEAT_001", "ENV_HARDWATER_001"]
  },
  "recovery_pathways": {
    "nutrition_restore": ["NUT_IRON_001", "NUT_PROTEIN_001", "NUT_ZINC_001"],
    "hormonal_correction": ["HOR_IGF1_001"],
    "sleep_repair": ["SLP_DEEPSLEEP_001"],
    "recovery_ref": "REC_FOLLICLE_001"
  },
  "cycle_phases": {
    "anagen": "2–7 years. Active growth. 85% of follicles at any time.",
    "catagen": "2–3 weeks. Controlled regression.",
    "telogen": "3–4 months. Rest phase. Shedding occurs at end."
  },
  "hair_fall_threshold": "Losing >100 hairs/day suggests disrupted anagen-telogen ratio."
}

{
  "id": "BIO_DERMALPAPILLA_001",
  "node_type": "biology",
  "version": "1.0",
  "structure": "Dermal Papilla",
  "parent_system": "SYS_HAIR_001",
  "definition": "Specialised mesenchymal cells at the base of the hair follicle that regulate hair growth signalling.",
  "function": "Acts as the command centre of the follicle. Sends growth signals to matrix cells. Receives hormonal and nutritional signals.",
  "molecular_mechanism": "Expresses androgen receptors. DHT binds here causing follicle miniaturisation via TGF-β upregulation and Wnt inhibition.",
  "damage_pathways": {
    "hormonal": ["HOR_DHT_001"],
    "inflammatory": ["INF_CHRONIC_001"]
  },
  "parent_biology": "BIO_FOLLICLE_001"
}

{
  "id": "BIO_HAIRBULB_001",
  "node_type": "biology",
  "version": "1.0",
  "structure": "Hair Bulb",
  "parent_system": "SYS_HAIR_001",
  "definition": "The base of the hair follicle containing the matrix cells and melanocytes.",
  "function": "Produces the hair shaft. Melanocytes within produce pigment (melanin).",
  "damage_pathways": {
    "nutritional": ["NUT_IRON_001", "NUT_COPPER_001"],
    "oxidative": ["OXI_FREE_RADICAL_001"]
  },
  "parent_biology": "BIO_FOLLICLE_001"
}

{
  "id": "BIO_MATRIX_001",
  "node_type": "biology",
  "version": "1.0",
  "structure": "Hair Matrix",
  "parent_system": "SYS_HAIR_001",
  "definition": "Rapidly dividing cells surrounding the dermal papilla that form the hair shaft.",
  "function": "Produces the cortex, cuticle, and medulla of the hair shaft through keratin synthesis.",
  "oxygen_dependence": "Matrix cells have one of the highest metabolic rates in the body. Highly sensitive to oxygen and nutrient supply.",
  "iron_mechanism": "Iron is required for ribonucleotide reductase — the rate-limiting enzyme for DNA synthesis in matrix cells. Iron deficiency → reduced cell division → premature telogen.",
  "damage_pathways": {
    "nutritional": ["NUT_IRON_001", "NUT_ZINC_001", "NUT_PROTEIN_001"],
    "hormonal": ["HOR_DHT_001"]
  },
  "parent_biology": "BIO_FOLLICLE_001"
}

{
  "id": "BIO_EPIDERMIS_001",
  "node_type": "biology",
  "version": "1.0",
  "structure": "Epidermis",
  "parent_system": "SYS_SKIN_001",
  "definition": "The outermost layer of skin, providing a physical barrier against pathogens, UV, and moisture loss.",
  "function": "Barrier protection, immune defence via Langerhans cells, UV absorption via melanocytes.",
  "layers": ["Stratum basale", "Stratum spinosum", "Stratum granulosum", "Stratum lucidum", "Stratum corneum"],
  "damage_pathways": {
    "nutritional": ["NUT_VITC_001", "NUT_ZINC_001"],
    "environmental": ["ENV_UV_001", "ENV_POLLUTION_001"],
    "inflammatory": ["INF_CHRONIC_001"]
  }
}

{
  "id": "BIO_DERMIS_001",
  "node_type": "biology",
  "version": "1.0",
  "structure": "Dermis",
  "parent_system": "SYS_SKIN_001",
  "definition": "The middle layer of skin containing collagen, elastin, blood vessels, and hair follicle roots.",
  "function": "Structural support, elasticity, wound healing, and nutrient delivery to epidermis.",
  "collagen_ref": "BIO_COLLAGEN_001",
  "damage_pathways": {
    "nutritional": ["NUT_VITC_001"],
    "hormonal": ["HOR_CORTISOL_001"],
    "oxidative": ["OXI_FREE_RADICAL_001"],
    "aging": ["LIF_AGING_001"]
  }
}

{
  "id": "BIO_COLLAGEN_001",
  "node_type": "biology",
  "version": "1.0",
  "structure": "Collagen Network",
  "parent_system": "SYS_SKIN_001",
  "definition": "Structural protein forming the scaffold of skin, tendons, and connective tissue.",
  "function": "Provides tensile strength and elasticity to skin.",
  "synthesis_requirements": ["NUT_VITC_001", "NUT_PROTEIN_001", "NUT_ZINC_001", "NUT_COPPER_001"],
  "damage_pathways": {
    "nutritional": ["NUT_VITC_001"],
    "hormonal": ["HOR_CORTISOL_001"],
    "oxidative": ["OXI_FREE_RADICAL_001"],
    "glycation": ["BLD_INSULIN_RESISTANCE_001"]
  }
}

{
  "id": "BIO_SEBGLAND_001",
  "node_type": "biology",
  "version": "1.0",
  "structure": "Sebaceous Gland",
  "parent_system": "SYS_SKIN_001",
  "definition": "Oil-producing gland attached to hair follicles, secreting sebum.",
  "function": "Sebum lubricates hair and skin, provides antimicrobial protection.",
  "regulation": "Directly regulated by androgens. DHT and testosterone increase sebum production.",
  "overactivity_effects": {
    "acne": "Excess sebum + blocked pore + bacteria = acne lesion",
    "oily_scalp": "Excess sebum blocks follicle opening"
  },
  "hormone_refs": ["HOR_DHT_001", "HOR_INSULIN_001"],
  "symptom_refs": ["SYM_ACNE_001", "SYM_OILYSKIN_001"]
}

{
  "id": "BIO_MITOCHONDRIA_001",
  "node_type": "biology",
  "version": "1.0",
  "structure": "Mitochondria",
  "parent_system": "SYS_ENERGY_001",
  "definition": "Cellular organelles responsible for producing ATP (cellular energy currency) via oxidative phosphorylation.",
  "function": "Generate 90% of cellular energy. Central to all tissue repair and growth.",
  "nutrient_dependence": ["NUT_IRON_001", "NUT_MAGNESIUM_001", "NUT_B12_001", "NUT_COENZYME_001"],
  "damage_pathways": {
    "oxidative": ["OXI_FREE_RADICAL_001"],
    "nutritional": ["NUT_IRON_001", "NUT_MAGNESIUM_001"],
    "inflammatory": ["INF_CHRONIC_001"]
  }
}

{
  "id": "BIO_THYROID_001",
  "node_type": "biology",
  "version": "1.0",
  "structure": "Thyroid Gland",
  "parent_system": "SYS_HORMONAL_001",
  "definition": "Butterfly-shaped gland in the neck producing thyroid hormones T3 and T4.",
  "function": "Regulates basal metabolic rate, heart rate, body temperature, and protein synthesis.",
  "hormone_produced": ["HOR_THYROID_001"],
  "regulation": "TSH from pituitary stimulates T4 production. T4 converts to active T3 in peripheral tissues.",
  "nutrient_dependence": ["NUT_IODINE_001", "NUT_SELENIUM_001", "NUT_IRON_001"],
  "damage_pathways": {
    "autoimmune": ["MED_HASHIMOTOS_001"],
    "nutritional": ["NUT_IODINE_001", "NUT_SELENIUM_001"]
  }
}

{
  "id": "BIO_MICROBIOME_001",
  "node_type": "biology",
  "version": "1.0",
  "structure": "Gut Microbiome",
  "parent_system": "SYS_DIGESTIVE_001",
  "definition": "Community of trillions of microorganisms in the gut with profound effects on nutrition, immunity, and hormones.",
  "function": "Synthesises B vitamins, short-chain fatty acids. Regulates immune response. Metabolises hormones (esp. estrogen via beta-glucuronidase).",
  "health_markers": ["species diversity", "Lactobacillus presence", "Bifidobacterium presence"],
  "damage_pathways": {
    "dietary": ["antibiotics", "high sugar", "low fibre", "ultra-processed food"],
    "stress": ["STR_CHRONIC_001"],
    "medications": ["MEDS_ANTIBIOTICS_001", "MEDS_PPIS_001"]
  },
  "downstream_effects": {
    "absorption": ["ABS_IRON_001", "ABS_B12_001", "ABS_ZINC_001"],
    "inflammation": ["INF_CHRONIC_001"],
    "hormones": ["HOR_ESTROGEN_001"]
  }
}

{
  "id": "BIO_GUTLINING_001",
  "node_type": "biology",
  "version": "1.0",
  "structure": "Intestinal Epithelial Lining",
  "parent_system": "SYS_DIGESTIVE_001",
  "definition": "Single-cell-thick barrier lining the intestine controlling what enters the bloodstream.",
  "function": "Selective absorption of nutrients. Barrier against pathogens and toxins.",
  "tight_junction_integrity": "Maintained by zinc, glutamine, and butyrate. Disrupted by inflammation, stress, alcohol.",
  "damage_pathways": {
    "nutritional": ["NUT_ZINC_001"],
    "stress": ["STR_CHRONIC_001"],
    "inflammatory": ["INF_CHRONIC_001"]
  },
  "leaky_gut_ref": "GUT_LEAKYGUT_001"
}

{
  "id": "BIO_ADRENAL_001",
  "node_type": "biology",
  "version": "1.0",
  "structure": "Adrenal Glands",
  "parent_system": "SYS_HORMONAL_001",
  "definition": "Glands sitting above kidneys producing cortisol, aldosterone, adrenaline, and DHEA.",
  "function": "Stress response, fluid balance, and androgen precursor production.",
  "hormone_produced": ["HOR_CORTISOL_001", "HOR_ADRENALINE_001", "HOR_DHEA_001"],
  "damage_pathways": {
    "chronic_stress": ["STR_CHRONIC_001"],
    "nutritional": ["NUT_VITC_001", "NUT_MAGNESIUM_001"]
  }
}
```

---

## 03_SYMPTOMS

**Purpose:** Defines what users experience and feel. Connects to biology and root causes. Never stores why — only what.

```json
{
  "id": "SYM_HAIRFALL_001",
  "node_type": "symptom",
  "version": "1.0",
  "name": "Hair Fall",
  "parent_system": "SYS_HAIR_001",
  "definition": "Loss of more than 100 hairs per day or visually noticeable reduction in hair density.",
  "severity_scale": {
    "mild": "Slightly more than usual hair on pillow, comb, or drain",
    "moderate": "Visible thinning, noticeable reduction in ponytail thickness",
    "severe": "Bald patches visible, scalp shows through hair"
  },
  "identification_patterns": [
    "Positive pull test (>6 hairs from 60-hair grab)",
    "Diffuse thinning across scalp",
    "Hairline recession (temples/crown)",
    "Circumscribed bald patches"
  ],
  "red_flags": [
    "Sudden patchy hair loss → refer dermatologist (alopecia areata possible)",
    "Hair loss with scaling/crusting → refer dermatologist",
    "Hair loss with systemic fatigue, cold intolerance → check thyroid",
    "Hair loss with heavy periods, fatigue → check ferritin",
    "Hair loss with acne + irregular periods → check for PCOS"
  ],
  "related_systems": ["SYS_HAIR_001", "SYS_HORMONAL_001", "SYS_ENERGY_001", "SYS_DIGESTIVE_001"],
  "root_cause_refs": [
    "RCE_IRON_HAIR_001",
    "RCE_DHT_HAIR_001",
    "RCE_THYROID_HAIR_001",
    "RCE_PCOS_HAIR_001",
    "RCE_PROTEIN_HAIR_001",
    "RCE_VITD_HAIR_001",
    "RCE_TELOGEN_HAIR_001"
  ],
  "symptom_cluster_refs": ["SCL_IRON_001", "SCL_PCOS_001", "SCL_THYROID_001"]
}

{
  "id": "SYM_HAIRTHIN_001",
  "node_type": "symptom",
  "version": "1.0",
  "name": "Hair Thinning",
  "parent_system": "SYS_HAIR_001",
  "definition": "Progressive reduction in individual hair shaft diameter without necessarily increased shedding.",
  "severity_scale": {
    "mild": "Hair feels finer, lacks volume",
    "moderate": "Noticeable reduction in hair thickness, scalp visible in parts",
    "severe": "Severe miniaturisation, vellus-like fine hairs"
  },
  "key_differentiator": "Thinning = miniaturised follicles. Hair Fall = excessive shedding. Both can coexist.",
  "primary_cause": "Follicle miniaturisation driven by DHT (androgenetic) or nutritional deficiency reducing shaft diameter.",
  "root_cause_refs": ["RCE_DHT_HAIR_001", "RCE_IRON_HAIR_001", "RCE_PROTEIN_HAIR_001"]
}

{
  "id": "SYM_ACNE_001",
  "node_type": "symptom",
  "version": "1.0",
  "name": "Acne",
  "parent_system": "SYS_SKIN_001",
  "definition": "Inflammatory skin condition characterised by comedones, papules, pustules, or cysts from blocked sebaceous glands.",
  "severity_scale": {
    "mild": "Blackheads/whiteheads only",
    "moderate": "Papules and pustules present",
    "severe": "Cysts, nodules, scarring"
  },
  "location_patterns": {
    "forehead_nose": "Gut / digestive imbalance",
    "jawline_chin": "Hormonal (PCOS, androgen excess)",
    "cheeks": "Dairy sensitivity, gut",
    "back_chest": "Hormonal or heat"
  },
  "root_cause_refs": ["RCE_DHT_SKIN_001", "RCE_INSULIN_ACNE_001", "RCE_GUT_ACNE_001"]
}

{
  "id": "SYM_FATIGUE_001",
  "node_type": "symptom",
  "version": "1.0",
  "name": "Fatigue",
  "parent_system": "SYS_ENERGY_001",
  "definition": "Persistent physical or mental tiredness not relieved by rest.",
  "severity_scale": {
    "mild": "Tired by evening, manageable with coffee",
    "moderate": "Tired throughout day, reduced productivity",
    "severe": "Cannot complete daily tasks, brain fog present"
  },
  "red_flags": [
    "Fatigue + cold intolerance + weight gain → check thyroid",
    "Fatigue + pallor + hair fall → check ferritin",
    "Fatigue + excessive thirst + urination → check HbA1c"
  ],
  "root_cause_refs": [
    "RCE_IRON_ENERGY_001",
    "RCE_THYROID_ENERGY_001",
    "RCE_B12_ENERGY_001",
    "RCE_VITD_ENERGY_001",
    "RCE_CORTISOL_ENERGY_001"
  ]
}

{
  "id": "SYM_BRAINFOG_001",
  "node_type": "symptom",
  "version": "1.0",
  "name": "Brain Fog",
  "parent_system": "SYS_ENERGY_001",
  "definition": "Cognitive difficulty characterised by poor concentration, memory lapses, slow thinking, and mental fatigue.",
  "root_cause_refs": ["RCE_IRON_ENERGY_001", "RCE_B12_ENERGY_001", "RCE_THYROID_ENERGY_001", "RCE_GUT_BRAIN_001"]
}

{
  "id": "SYM_WEIGHTGAIN_001",
  "node_type": "symptom",
  "version": "1.0",
  "name": "Unexplained Weight Gain",
  "parent_system": "SYS_WEIGHT_001",
  "definition": "Weight gain without proportionate increase in caloric intake.",
  "red_flags": [
    "Weight gain + hair fall + fatigue → check thyroid",
    "Weight gain + irregular periods + acne → check PCOS/insulin",
    "Weight gain + excessive thirst → check HbA1c"
  ],
  "root_cause_refs": ["RCE_THYROID_WEIGHT_001", "RCE_PCOS_WEIGHT_001", "RCE_INSULIN_WEIGHT_001"]
}

{
  "id": "SYM_POORSLEEP_001",
  "node_type": "symptom",
  "version": "1.0",
  "name": "Poor Sleep",
  "parent_system": "SYS_SLEEP_001",
  "definition": "Difficulty falling asleep, staying asleep, or feeling unrefreshed after sleep.",
  "root_cause_refs": ["RCE_CORTISOL_SLEEP_001", "RCE_MAGNESIUM_SLEEP_001", "RCE_THYROID_SLEEP_001"]
}

{
  "id": "SYM_BLOATING_001",
  "node_type": "symptom",
  "version": "1.0",
  "name": "Bloating",
  "parent_system": "SYS_DIGESTIVE_001",
  "definition": "Abdominal distension and discomfort from gas or fluid accumulation.",
  "root_cause_refs": ["RCE_DYSBIOSIS_GUT_001", "RCE_LEAKYGUT_001"]
}

{
  "id": "SYM_DRYSKIN_001",
  "node_type": "symptom",
  "version": "1.0",
  "name": "Dry Skin",
  "parent_system": "SYS_SKIN_001",
  "definition": "Rough, flaky, or tight skin due to insufficient moisture or barrier dysfunction.",
  "root_cause_refs": ["RCE_VITD_SKIN_001", "RCE_OMEGA3_SKIN_001", "RCE_THYROID_SKIN_001", "RCE_HYDRATION_SKIN_001"]
}

{
  "id": "SYM_IRREGULARPERIODS_001",
  "node_type": "symptom",
  "version": "1.0",
  "name": "Irregular Periods",
  "parent_system": "SYS_HORMONAL_001",
  "definition": "Menstrual cycles shorter than 21 days or longer than 35 days, or variable in duration.",
  "red_flags": [
    "Irregular periods + hair fall + acne → check PCOS",
    "Irregular periods + weight gain + insulin resistance → check metabolic panel"
  ],
  "root_cause_refs": ["RCE_PCOS_001", "RCE_THYROID_HORMONAL_001", "RCE_STRESS_HORMONAL_001"]
}
```

---

## 04_NUTRITION

**Purpose:** Single source of truth for all nutrient biology. Never store nutrient information anywhere else.

```json
{
  "id": "NUT_IRON_001",
  "node_type": "nutrition",
  "version": "1.0",
  "nutrient": "Iron",
  "type": "mineral",
  "forms": ["Heme iron (animal)", "Non-heme iron (plant)"],
  "functions": [
    "Oxygen transport via haemoglobin in red blood cells",
    "Electron transport chain — ATP production in mitochondria",
    "Ribonucleotide reductase — rate-limiting enzyme for DNA synthesis",
    "Thyroid hormone synthesis cofactor",
    "Collagen synthesis support",
    "Neurotransmitter synthesis (dopamine, serotonin)"
  ],
  "deficiency_effects": {
    "hair": "Reduced O2 to matrix → slow cell division → premature telogen → diffuse shedding",
    "skin": "Pallor, poor wound healing, reduced collagen support",
    "energy": "Anaerobic shift → lactic acid buildup → fatigue, brain fog",
    "cognitive": "Dopamine dysregulation → poor concentration",
    "immune": "Reduced T-cell activity"
  },
  "food_sources": {
    "heme": [
      { "food_ref": "FOD_CHICKEN_LIVER_001", "mg_per_100g": 9.0 },
      { "food_ref": "FOD_MUTTON_001", "mg_per_100g": 3.1 },
      { "food_ref": "FOD_EGG_YOLK_001", "mg_per_100g": 2.7 }
    ],
    "non_heme": [
      { "food_ref": "FOD_SPINACH_001", "mg_per_100g": 2.7 },
      { "food_ref": "FOD_RAJMA_001", "mg_per_100g": 8.2, "note": "Cooked" },
      { "food_ref": "FOD_JAGGERY_001", "mg_per_100g": 11.0 },
      { "food_ref": "FOD_SESAME_001", "mg_per_100g": 14.6 },
      { "food_ref": "FOD_POMEGRANATE_001", "mg_per_100g": 0.3, "note": "Low but high in Vit C, enhances absorption" }
    ]
  },
  "absorption_ref": "ABS_IRON_001",
  "lab_markers": ["LAB_FERRITIN_001", "LAB_SERUM_IRON_001", "LAB_TRANSFERRIN_001", "LAB_TIBC_001", "LAB_CBC_001"],
  "hair_optimal_range": "Ferritin > 70 ng/mL for active hair growth support",
  "rda": { "women_19_50": "18 mg/day", "pregnant": "27 mg/day", "men": "8 mg/day" },
  "tags": ["iron", "ferritin", "anaemia", "hair", "energy", "oxygen"]
}

{
  "id": "NUT_ZINC_001",
  "node_type": "nutrition",
  "version": "1.0",
  "nutrient": "Zinc",
  "type": "mineral",
  "functions": [
    "5-alpha reductase inhibition (reduces DHT conversion)",
    "Keratin synthesis — structural protein of hair shaft",
    "Wound healing and collagen synthesis",
    "Immune function regulation",
    "Sebum regulation in sebaceous glands",
    "Enzyme cofactor (300+ enzymes)"
  ],
  "deficiency_effects": {
    "hair": "Impaired keratin → weak shaft → breakage; reduced 5AR inhibition → more DHT",
    "skin": "Poor wound healing, acne, stretch marks",
    "immune": "Increased susceptibility to infection",
    "gut": "Disrupted tight junctions → leaky gut"
  },
  "food_sources": [
    { "food_ref": "FOD_PUMPKIN_SEEDS_001", "mg_per_100g": 7.8 },
    { "food_ref": "FOD_CHICKPEA_001", "mg_per_100g": 1.5 },
    { "food_ref": "FOD_CASHEW_001", "mg_per_100g": 5.8 },
    { "food_ref": "FOD_MUTTON_001", "mg_per_100g": 4.5 }
  ],
  "absorption_ref": "ABS_ZINC_001",
  "lab_markers": ["LAB_SERUM_ZINC_001"],
  "rda": { "women": "8 mg/day", "men": "11 mg/day" },
  "tags": ["zinc", "DHT", "keratin", "hair", "skin", "wound healing"]
}

{
  "id": "NUT_VITD_001",
  "node_type": "nutrition",
  "version": "1.0",
  "nutrient": "Vitamin D",
  "type": "fat_soluble_vitamin",
  "functions": [
    "Vitamin D receptor (VDR) in hair follicle bulge — initiates anagen phase",
    "Calcium absorption regulation",
    "Immune modulation — reduces autoimmune risk",
    "Mood regulation — serotonin synthesis",
    "Muscle function"
  ],
  "deficiency_effects": {
    "hair": "VDR underactivation → follicle fails to re-enter anagen → chronic telogen",
    "immune": "Increased autoimmune risk (Hashimoto's, alopecia areata)",
    "mood": "Depression, low motivation",
    "bone": "Reduced calcium absorption → osteoporosis risk"
  },
  "food_sources": [
    { "food_ref": "FOD_FATTY_FISH_001", "iu_per_100g": 600 },
    { "food_ref": "FOD_EGG_YOLK_001", "iu_per_100g": 37 }
  ],
  "synthesis": "Sunlight (UVB) on skin converts 7-dehydrocholesterol → pre-Vitamin D3",
  "absorption_ref": "ABS_VITD_001",
  "lab_markers": ["LAB_VITD_001"],
  "optimal_range_hair": "50–80 ng/mL for hair and immune health",
  "rda": "600–800 IU/day (standard). Deficient individuals often need 2000–4000 IU/day under supervision.",
  "tags": ["vitamin D", "VDR", "hair", "immune", "bone", "mood"]
}

{
  "id": "NUT_B12_001",
  "node_type": "nutrition",
  "version": "1.0",
  "nutrient": "Vitamin B12",
  "type": "water_soluble_vitamin",
  "functions": [
    "Red blood cell maturation",
    "Myelin sheath synthesis for nerve conduction",
    "DNA synthesis and cell replication",
    "Homocysteine metabolism (cardiovascular protection)"
  ],
  "deficiency_effects": {
    "hair": "Impaired RBC maturation → reduced O2 delivery → similar to iron deficiency hair loss",
    "energy": "Megaloblastic anaemia → severe fatigue",
    "neurological": "Peripheral neuropathy, brain fog, memory issues",
    "skin": "Hyperpigmentation, premature greying"
  },
  "food_sources": [
    { "food_ref": "FOD_EGG_001", "mcg_per_100g": 1.1 },
    { "food_ref": "FOD_MILK_001", "mcg_per_100g": 0.4 },
    { "food_ref": "FOD_MUTTON_001", "mcg_per_100g": 2.6 }
  ],
  "risk_groups": ["Vegetarians", "Vegans", "PPI users", "Metformin users", "Post-gastric surgery"],
  "absorption_ref": "ABS_B12_001",
  "lab_markers": ["LAB_B12_001", "LAB_MCV_001", "LAB_HOMOCYSTEINE_001"],
  "rda": "2.4 mcg/day",
  "tags": ["B12", "anaemia", "neurological", "hair", "energy"]
}

{
  "id": "NUT_PROTEIN_001",
  "node_type": "nutrition",
  "version": "1.0",
  "nutrient": "Protein",
  "type": "macronutrient",
  "functions": [
    "Hair shaft synthesis (keratin is 95% protein)",
    "Muscle repair and synthesis",
    "Enzyme production",
    "Collagen synthesis",
    "Immune antibody production"
  ],
  "deficiency_effects": {
    "hair": "Keratin deficiency → weak, brittle hair → telogen effluvium",
    "muscle": "Muscle wasting, fatigue",
    "immune": "Reduced antibody production",
    "skin": "Poor wound healing, reduced collagen"
  },
  "food_sources": [
    { "food_ref": "FOD_DAL_001", "g_protein_per_100g": 9.0 },
    { "food_ref": "FOD_PANEER_001", "g_protein_per_100g": 18.0 },
    { "food_ref": "FOD_EGG_001", "g_protein_per_100g": 13.0 },
    { "food_ref": "FOD_CHICKPEA_001", "g_protein_per_100g": 19.0 }
  ],
  "rda": "0.8 g/kg body weight (minimum). Active individuals: 1.2–2.0 g/kg.",
  "tags": ["protein", "keratin", "hair", "muscle", "collagen"]
}

{
  "id": "NUT_OMEGA3_001",
  "node_type": "nutrition",
  "version": "1.0",
  "nutrient": "Omega-3 Fatty Acids",
  "type": "essential_fat",
  "forms": ["EPA", "DHA", "ALA"],
  "functions": [
    "Anti-inflammatory pathway regulation (reduces PGE2)",
    "Skin barrier lipid composition",
    "Scalp circulation support",
    "Brain and mood regulation",
    "Cardiovascular protection"
  ],
  "deficiency_effects": {
    "hair": "Dry, brittle hair, scalp flakiness, poor follicle circulation",
    "skin": "Dry, flaky, inflamed skin, poor barrier",
    "mood": "Depression, anxiety risk"
  },
  "food_sources": [
    { "food_ref": "FOD_FLAXSEED_001", "g_per_tbsp": 2.4, "type": "ALA" },
    { "food_ref": "FOD_WALNUT_001", "g_per_30g": 2.5, "type": "ALA" },
    { "food_ref": "FOD_FATTY_FISH_001", "g_per_100g": 2.5, "type": "EPA+DHA" }
  ],
  "tags": ["omega-3", "anti-inflammatory", "skin", "hair", "brain"]
}

{
  "id": "NUT_MAGNESIUM_001",
  "node_type": "nutrition",
  "version": "1.0",
  "nutrient": "Magnesium",
  "type": "mineral",
  "functions": [
    "ATP synthesis cofactor (energy production)",
    "Sleep regulation — GABA receptor agonist",
    "Insulin sensitivity improvement",
    "300+ enzyme cofactor",
    "Stress regulation — cortisol buffering",
    "Muscle relaxation"
  ],
  "deficiency_effects": {
    "hair": "Indirect — via elevated cortisol and insulin resistance → hormonal imbalance → hair loss",
    "sleep": "Disrupted GABA signalling → poor sleep",
    "energy": "Impaired ATP synthesis → fatigue",
    "stress": "Elevated cortisol response"
  },
  "food_sources": [
    { "food_ref": "FOD_PUMPKIN_SEEDS_001", "mg_per_100g": 592 },
    { "food_ref": "FOD_SPINACH_001", "mg_per_100g": 79 },
    { "food_ref": "FOD_BANANA_001", "mg_per_100g": 27 }
  ],
  "lab_markers": ["LAB_SERUM_MAGNESIUM_001"],
  "rda": { "women": "310–320 mg/day", "men": "400–420 mg/day" },
  "tags": ["magnesium", "sleep", "energy", "stress", "insulin"]
}

{
  "id": "NUT_SELENIUM_001",
  "node_type": "nutrition",
  "version": "1.0",
  "nutrient": "Selenium",
  "type": "trace_mineral",
  "functions": [
    "Thyroid hormone conversion (T4 → T3) via deiodinase enzymes",
    "Antioxidant — glutathione peroxidase cofactor",
    "Immune function",
    "Anti-inflammatory"
  ],
  "deficiency_effects": {
    "thyroid": "Impaired T4→T3 conversion → hypothyroid symptoms without TSH change",
    "hair": "Secondary via thyroid → hair loss, thinning",
    "antioxidant": "Increased oxidative stress"
  },
  "food_sources": [
    { "food_ref": "FOD_BRAZIL_NUT_001", "mcg_per_nut": 96 },
    { "food_ref": "FOD_EGG_001", "mcg_per_100g": 30 }
  ],
  "lab_markers": ["LAB_SERUM_SELENIUM_001"],
  "rda": "55 mcg/day",
  "tags": ["selenium", "thyroid", "antioxidant", "T3", "T4"]
}

{
  "id": "NUT_BIOTIN_001",
  "node_type": "nutrition",
  "version": "1.0",
  "nutrient": "Biotin (Vitamin B7)",
  "type": "water_soluble_vitamin",
  "functions": [
    "Fatty acid synthesis",
    "Amino acid metabolism",
    "Keratin infrastructure support"
  ],
  "deficiency_effects": {
    "hair": "True biotin deficiency → brittle hair and nails. Rare in healthy individuals.",
    "skin": "Seborrheic dermatitis-like rash"
  },
  "important_note": "True biotin deficiency is RARE. Most hair loss labelled as 'biotin deficiency' is actually iron, zinc, or protein deficiency. Raw egg white consumption blocks biotin absorption (avidin binding).",
  "food_sources": [
    { "food_ref": "FOD_EGG_YOLK_001", "mcg_per_100g": 53 },
    { "food_ref": "FOD_PEANUT_001", "mcg_per_100g": 17 }
  ],
  "tags": ["biotin", "keratin", "hair", "nails"]
}

{
  "id": "NUT_VITC_001",
  "node_type": "nutrition",
  "version": "1.0",
  "nutrient": "Vitamin C",
  "type": "water_soluble_vitamin",
  "functions": [
    "Iron absorption enhancer — reduces Fe3+ to Fe2+ for DMT-1 uptake",
    "Collagen synthesis cofactor — hydroxylation of proline and lysine",
    "Antioxidant — neutralises free radicals",
    "Adrenal cortisol regulation"
  ],
  "deficiency_effects": {
    "hair": "Impaired collagen → poor follicle structure; impaired iron absorption → iron deficiency",
    "skin": "Poor collagen → wrinkles, poor wound healing",
    "immune": "Reduced immune defence"
  },
  "food_sources": [
    { "food_ref": "FOD_AMLA_001", "mg_per_100g": 600 },
    { "food_ref": "FOD_GUAVA_001", "mg_per_100g": 228 },
    { "food_ref": "FOD_LEMON_001", "mg_per_100g": 53 }
  ],
  "tags": ["vitamin C", "iron absorption", "collagen", "antioxidant"]
}
```

---

## 05_ABSORPTION

**Purpose:** Defines how and when nutrients are absorbed. Blockers and enhancers stored ONLY here.

```json
{
  "id": "ABS_IRON_001",
  "node_type": "absorption",
  "version": "1.0",
  "nutrient_ref": "NUT_IRON_001",
  "absorption_site": "Duodenum and upper jejunum",
  "enhancers": [
    { "item": "Vitamin C (50mg+)", "mechanism": "Reduces Fe3+ to Fe2+, required for DMT-1 transporter", "ref": "NUT_VITC_001" },
    { "item": "Meat factor", "mechanism": "Heme iron absorbed 15–35% vs 2–20% non-heme" },
    { "item": "Acidic environment", "mechanism": "Low gastric pH enhances non-heme solubility" },
    { "item": "Cooking in iron vessels", "mechanism": "Leaches elemental iron into food" }
  ],
  "blockers": [
    { "item": "Tannins (tea/coffee)", "mechanism": "Binds iron, forms insoluble complex", "advice": "Wait 1 hour before/after iron meal" },
    { "item": "Phytates (unleavened grains)", "mechanism": "Chelates iron in gut lumen", "advice": "Soak legumes overnight, ferment grains" },
    { "item": "Calcium (dairy)", "mechanism": "Competes with iron at DMT-1 transporter", "advice": "Separate dairy from iron-rich meals" },
    { "item": "Antacids/PPIs", "mechanism": "Raise gastric pH, reduce non-heme solubility", "ref": "MEDS_PPIS_001" }
  ],
  "transport_mechanism": "DMT-1 (Divalent Metal Transporter 1) for non-heme Fe2+. Heme absorbed via separate HCP1 transporter. Transferred to blood via ferroportin.",
  "gut_dependence": true,
  "gut_ref": "GUT_MALABSORPTION_001",
  "special_notes": [
    "H. pylori infection disrupts gastric acid → impairs iron absorption significantly",
    "Celiac disease causes duodenal damage → severely impairs iron absorption"
  ]
}

{
  "id": "ABS_B12_001",
  "node_type": "absorption",
  "version": "1.0",
  "nutrient_ref": "NUT_B12_001",
  "absorption_site": "Terminal ileum",
  "mechanism": "B12 binds intrinsic factor (IF) produced by gastric parietal cells. IF-B12 complex absorbed in ileum via cubilin receptor.",
  "blockers": [
    { "item": "PPIs/H2 blockers", "mechanism": "Reduce gastric acid → impaired IF release", "ref": "MEDS_PPIS_001" },
    { "item": "Metformin", "mechanism": "Disrupts IF-B12 absorption at ileum", "ref": "MEDS_METFORMIN_001" },
    { "item": "Pernicious anaemia", "mechanism": "Autoimmune destruction of parietal cells → no IF produced" }
  ],
  "risk_groups": ["Strict vegetarians (no dietary B12)", "PPI users >12 months", "Metformin users", "Post-bariatric surgery"],
  "gut_dependence": true,
  "gut_ref": "GUT_MALABSORPTION_001"
}

{
  "id": "ABS_ZINC_001",
  "node_type": "absorption",
  "version": "1.0",
  "nutrient_ref": "NUT_ZINC_001",
  "absorption_site": "Small intestine",
  "blockers": [
    { "item": "Phytates (legumes, grains)", "mechanism": "Forms zinc-phytate complex, reduces absorption by 50%" },
    { "item": "High calcium intake", "mechanism": "Competes with zinc absorption" },
    { "item": "High iron supplementation", "mechanism": "Competes at same transporter" }
  ],
  "enhancers": [
    { "item": "Protein", "mechanism": "Amino acids chelate zinc, enhance absorption" },
    { "item": "Soaking/sprouting legumes", "mechanism": "Reduces phytate content" }
  ],
  "gut_dependence": true
}

{
  "id": "ABS_VITD_001",
  "node_type": "absorption",
  "version": "1.0",
  "nutrient_ref": "NUT_VITD_001",
  "absorption_type": "Fat-soluble — requires dietary fat for absorption",
  "enhancers": [
    { "item": "Dietary fat (same meal)", "mechanism": "Incorporates into chylomicrons for lymphatic absorption" },
    { "item": "Magnesium", "mechanism": "Required for Vitamin D activation enzymes (hydroxylation)", "ref": "NUT_MAGNESIUM_001" }
  ],
  "blockers": [
    { "item": "Fat malabsorption", "mechanism": "Celiac, Crohn's, pancreatic insufficiency impair fat-soluble vitamin uptake" },
    { "item": "Obesity", "mechanism": "Sequestration in adipose tissue reduces bioavailability" }
  ],
  "activation": "Liver: 25-hydroxylation → 25(OH)D. Kidney: 1-alpha-hydroxylation → active 1,25(OH)2D.",
  "synthesis_route": "Sunlight UVB → 7-dehydrocholesterol → pre-D3 → D3 in skin"
}
```

---

## 06_GUT_HEALTH

```json
{
  "id": "GUT_DYSBIOSIS_001",
  "node_type": "gut_health",
  "version": "1.0",
  "condition": "Dysbiosis",
  "definition": "Qualitative or quantitative imbalance of the gut microbiome with reduction of beneficial species.",
  "causes": [
    "Antibiotic use (ref: MEDS_ANTIBIOTICS_001)",
    "High sugar/ultra-processed diet",
    "Chronic stress (ref: STR_CHRONIC_001)",
    "Low dietary fibre",
    "Alcohol consumption"
  ],
  "downstream_effects": {
    "absorption_impairment": ["ABS_IRON_001", "ABS_B12_001", "ABS_ZINC_001"],
    "inflammation": "INF_CHRONIC_001",
    "gut_permeability": "GUT_LEAKYGUT_001",
    "hormone_disruption": "Enterohepatic circulation of estrogen disrupted — affects HOR_ESTROGEN_001",
    "symptom_refs": ["SYM_BLOATING_001", "SYM_BRAINFOG_001", "SYM_HAIRFALL_001", "SYM_ACNE_001"]
  },
  "gut_brain_axis": "Dysbiosis → altered serotonin production (90% made in gut) → mood, brain fog",
  "gut_skin_axis": "Dysbiosis → systemic inflammation → acne, eczema, psoriasis flares"
}

{
  "id": "GUT_LEAKYGUT_001",
  "node_type": "gut_health",
  "version": "1.0",
  "condition": "Increased Intestinal Permeability (Leaky Gut)",
  "definition": "Breakdown of tight junction proteins allowing bacterial endotoxins (LPS) and undigested particles to enter bloodstream.",
  "causes": ["Dysbiosis (ref: GUT_DYSBIOSIS_001)", "Chronic stress", "Alcohol", "NSAIDs", "Gluten in susceptible individuals"],
  "downstream_effects": {
    "inflammation": "LPS triggers systemic low-grade inflammation via TLR4 receptors — ref: INF_CHRONIC_001",
    "autoimmune_risk": "Molecular mimicry → increased autoimmune triggers",
    "skin": "Systemic inflammation → acne, rosacea, eczema",
    "nutrient_loss": "Damaged villi reduce absorptive surface area"
  },
  "biology_ref": "BIO_GUTLINING_001"
}

{
  "id": "GUT_MALABSORPTION_001",
  "node_type": "gut_health",
  "version": "1.0",
  "condition": "Nutrient Malabsorption",
  "definition": "Impaired absorption of one or more nutrients due to gut pathology or dysfunction.",
  "causes": [
    "Dysbiosis (ref: GUT_DYSBIOSIS_001)",
    "Leaky gut (ref: GUT_LEAKYGUT_001)",
    "Celiac disease",
    "H. pylori infection",
    "Low stomach acid (hypochlorhydria)"
  ],
  "affected_nutrients": ["NUT_IRON_001", "NUT_B12_001", "NUT_ZINC_001", "NUT_VITD_001"],
  "symptom_refs": ["SYM_FATIGUE_001", "SYM_HAIRFALL_001", "SYM_BRAINFOG_001"]
}

{
  "id": "GUT_IBS_001",
  "node_type": "gut_health",
  "version": "1.0",
  "condition": "Irritable Bowel Syndrome",
  "definition": "Functional bowel disorder with abdominal pain, bloating, altered bowel habits without structural damage.",
  "subtypes": ["IBS-C (constipation dominant)", "IBS-D (diarrhoea dominant)", "IBS-M (mixed)"],
  "causes": ["Gut dysbiosis", "Stress-gut axis dysregulation", "Post-infectious", "Food sensitivities"],
  "downstream_effects": {
    "absorption": "GUT_MALABSORPTION_001",
    "inflammation": "INF_CHRONIC_001",
    "symptoms": ["SYM_BLOATING_001", "SYM_FATIGUE_001"]
  }
}
```

---

## 07_HORMONES

```json
{
  "id": "HOR_DHT_001",
  "node_type": "hormone",
  "version": "1.0",
  "name": "DHT (Dihydrotestosterone)",
  "class": "androgen",
  "production_pathway": "Testosterone → 5-alpha reductase (Type I, II) enzyme → DHT",
  "production_sites": ["Prostate", "Skin", "Liver", "Hair follicles"],
  "functions": ["Male secondary sexual development", "Prostate growth", "Libido"],
  "imbalance": {
    "excess": {
      "causes": [
        "High testosterone (PCOS, steroid use)",
        "High 5-alpha reductase activity (genetic)",
        "Insulin resistance (increases androgen production)",
        "Low SHBG (more free testosterone → more DHT)"
      ],
      "effects": {
        "hair": "Binds AR in dermal papilla → TGF-β upregulation → Wnt inhibition → follicle miniaturisation → androgenetic alopecia",
        "skin": "Sebaceous gland hyperactivity → excess sebum → acne",
        "prostate": "BPH in older males"
      }
    }
  },
  "natural_inhibitors": [
    { "item": "Zinc", "ref": "NUT_ZINC_001", "mechanism": "Inhibits 5-alpha reductase enzyme" },
    { "item": "Saw Palmetto", "mechanism": "5-alpha reductase inhibitor (supplement)" },
    { "item": "Green tea EGCG", "mechanism": "5-alpha reductase inhibition" }
  ],
  "symptom_refs": ["SYM_HAIRFALL_001", "SYM_HAIRTHIN_001", "SYM_ACNE_001"],
  "lab_markers": ["LAB_FREE_TESTOSTERONE_001", "LAB_TOTAL_TESTOSTERONE_001", "LAB_SHBG_001"],
  "genetics_ref": "GEN_ANDROGEN_SENSITIVITY_001"
}

{
  "id": "HOR_CORTISOL_001",
  "node_type": "hormone",
  "version": "1.0",
  "name": "Cortisol",
  "class": "glucocorticoid",
  "production": "Adrenal cortex (zona fasciculata) → regulated by CRH → ACTH cascade",
  "normal_pattern": "Highest at 6–8 AM, lowest at midnight",
  "functions": ["Stress response", "Blood glucose regulation", "Anti-inflammatory (acute)", "Memory consolidation"],
  "imbalance": {
    "chronically_elevated": {
      "causes": ["Chronic stress (ref: STR_CHRONIC_001)", "Sleep deprivation", "Blood sugar dysregulation"],
      "effects": {
        "hair": "Prolongs telogen, inhibits anagen entry → diffuse shedding (telogen effluvium)",
        "skin": "Collagen degradation → thinning, poor healing",
        "immune": "Immunosuppression → increased infection risk",
        "gut": "Increased gut permeability (ref: GUT_LEAKYGUT_001)",
        "weight": "Promotes visceral fat storage, insulin resistance",
        "sleep": "Suppresses melatonin → disrupts sleep architecture"
      }
    }
  },
  "lab_markers": ["LAB_MORNING_CORTISOL_001", "LAB_DHEA_001"],
  "symptom_refs": ["SYM_HAIRFALL_001", "SYM_FATIGUE_001", "SYM_WEIGHTGAIN_001", "SYM_POORSLEEP_001"],
  "biology_ref": "BIO_ADRENAL_001"
}

{
  "id": "HOR_INSULIN_001",
  "node_type": "hormone",
  "version": "1.0",
  "name": "Insulin",
  "class": "peptide_hormone",
  "production": "Pancreatic beta cells",
  "functions": ["Glucose uptake into cells", "Glycogen synthesis", "Protein anabolism", "Fat storage"],
  "imbalance": {
    "insulin_resistance": {
      "definition": "Cells become resistant to insulin → compensatory hyperinsulinemia",
      "causes": ["High glycaemic diet", "Obesity", "Physical inactivity", "Chronic stress", "Sleep deprivation"],
      "effects": {
        "hormonal": "Stimulates ovarian androgen production → PCOS",
        "skin": "IGF-1 stimulation → sebum overproduction → acne; skin tags, acanthosis nigricans",
        "weight": "Promotes fat storage, blocks lipolysis",
        "hair": "Via androgen excess → DHT → hair loss"
      }
    }
  },
  "blood_sugar_ref": "BLD_INSULIN_RESISTANCE_001",
  "lab_markers": ["LAB_FASTING_INSULIN_001", "LAB_HOMA_IR_001", "LAB_HBA1C_001", "LAB_FASTING_GLUCOSE_001"],
  "symptom_refs": ["SYM_ACNE_001", "SYM_WEIGHTGAIN_001", "SYM_FATIGUE_001"]
}

{
  "id": "HOR_THYROID_001",
  "node_type": "hormone",
  "version": "1.0",
  "name": "Thyroid Hormones (T3 / T4)",
  "class": "iodothyronine",
  "production": "T4 (thyroxine) produced by thyroid gland. T4 → T3 (active form) converted in periphery via deiodinase (requires selenium).",
  "functions": ["Basal metabolic rate regulation", "Protein synthesis", "Heart rate", "Body temperature", "Hair cycle regulation"],
  "imbalance": {
    "hypothyroid": {
      "causes": ["Hashimoto's thyroiditis (autoimmune)", "Iodine deficiency", "Selenium deficiency", "Postpartum thyroiditis"],
      "effects": {
        "hair": "Slows anagen phase, impairs follicle cell metabolism → diffuse hair loss, outer eyebrow loss",
        "skin": "Myxoedema, dry rough skin, puffy face",
        "energy": "Fatigue, cold intolerance, brain fog",
        "weight": "Weight gain, constipation"
      }
    },
    "hyperthyroid": {
      "effects": {
        "hair": "Accelerated hair cycling → diffuse loss",
        "energy": "Anxiety, palpitations, heat intolerance",
        "weight": "Unexplained weight loss"
      }
    }
  },
  "lab_markers": ["LAB_TSH_001", "LAB_FT3_001", "LAB_FT4_001", "LAB_ANTI_TPO_001"],
  "nutrition_refs": ["NUT_IODINE_001", "NUT_SELENIUM_001"],
  "symptom_refs": ["SYM_HAIRFALL_001", "SYM_FATIGUE_001", "SYM_WEIGHTGAIN_001", "SYM_DRYSKIN_001"]
}

{
  "id": "HOR_ESTROGEN_001",
  "node_type": "hormone",
  "version": "1.0",
  "name": "Estrogen",
  "class": "steroid_hormone",
  "forms": ["Estrone (E1)", "Estradiol (E2)", "Estriol (E3)"],
  "production": "Ovaries (primary), adipose tissue, adrenal glands. Liver metabolises and inactivates.",
  "functions": ["Uterine lining growth", "Breast development", "Bone density maintenance", "Cardiovascular protection", "Prolongs anagen phase of hair"],
  "imbalance": {
    "low_estrogen": {
      "causes": ["Menopause", "POI", "Extreme caloric restriction", "Overtraining"],
      "effects": {
        "hair": "Loss of anagen-prolonging effect → diffuse thinning",
        "skin": "Thinning, dryness, increased wrinkles",
        "bone": "Increased osteoporosis risk",
        "mood": "Depression, brain fog"
      }
    },
    "estrogen_dominance": {
      "causes": ["Gut dysbiosis → impaired enterohepatic clearance", "Liver stress", "Xenoestrogen exposure", "Progesterone deficiency"],
      "effects": {
        "hair": "Paradoxical hair loss in some",
        "weight": "Water retention, fat gain around hips",
        "periods": "Heavy periods, clots, PMS"
      }
    }
  },
  "gut_connection": "GUT_DYSBIOSIS_001 → impaired beta-glucuronidase regulation → estrogen recirculation",
  "lab_markers": ["LAB_ESTRADIOL_001"],
  "life_stages_ref": ["LIF_MENOPAUSE_001", "LIF_PREGNANCY_001", "LIF_POSTPARTUM_001"]
}

{
  "id": "HOR_IGF1_001",
  "node_type": "hormone",
  "version": "1.0",
  "name": "IGF-1 (Insulin-like Growth Factor 1)",
  "class": "growth_factor",
  "production": "Liver (primary), stimulated by Growth Hormone",
  "functions": ["Stimulates anagen phase of hair follicle", "Muscle protein synthesis", "Cell proliferation and survival"],
  "imbalance": {
    "low_IGF1": {
      "causes": ["Poor sleep (GH released in deep sleep)", "Malnutrition", "Liver dysfunction"],
      "effects": {
        "hair": "Impaired anagen initiation → shorter growth phase",
        "muscle": "Reduced muscle mass"
      }
    }
  },
  "sleep_ref": "SLP_DEEPSLEEP_001",
  "symptom_refs": ["SYM_HAIRFALL_001", "SYM_HAIRTHIN_001"]
}
```

---

## 08_SLEEP

```json
{
  "id": "SLP_BIOLOGY_001",
  "node_type": "sleep",
  "version": "1.0",
  "topic": "Sleep Biology Overview",
  "sleep_architecture": {
    "stages": [
      { "stage": "N1", "name": "Light sleep", "duration_pct": "5%" },
      { "stage": "N2", "name": "Confirmed sleep, sleep spindles", "duration_pct": "45%" },
      { "stage": "N3", "name": "Slow-wave / deep sleep — repair phase", "duration_pct": "25%" },
      { "stage": "REM", "name": "Dreaming, memory consolidation", "duration_pct": "25%" }
    ]
  },
  "repair_hormones": ["HOR_GH_001 (Growth hormone — peaks in N3)", "HOR_MELATONIN_001"],
  "hair_connection": "N3 deep sleep → GH surge → IGF-1 production → anagen support (ref: HOR_IGF1_001)",
  "immune_connection": "Deep sleep → cytokine regulation → anti-inflammatory effects",
  "symptom_refs": ["SYM_FATIGUE_001", "SYM_HAIRFALL_001", "SYM_BRAINFOG_001"]
}

{
  "id": "SLP_CIRCADIAN_001",
  "node_type": "sleep",
  "version": "1.0",
  "topic": "Circadian Rhythm",
  "definition": "24-hour internal clock governing sleep-wake cycles, hormone release, and metabolic processes.",
  "master_clock": "Suprachiasmatic nucleus (SCN) in hypothalamus",
  "key_signals": ["Morning light → suppresses melatonin, raises cortisol (healthy AM peak)", "Evening darkness → melatonin secretion begins"],
  "disruption_causes": ["Blue light exposure post 9 PM", "Irregular sleep schedule", "Night shift work", "Late eating"],
  "disruption_effects": {
    "hormonal": "Cortisol pattern inversion → elevated evening cortisol (ref: HOR_CORTISOL_001)",
    "hair": "Disrupted GH release → poor IGF-1 → impaired follicle support",
    "metabolic": "Glucose tolerance worsens → insulin resistance (ref: BLD_INSULIN_RESISTANCE_001)"
  }
}

{
  "id": "SLP_DEEPSLEEP_001",
  "node_type": "sleep",
  "version": "1.0",
  "topic": "Deep Sleep (Slow-Wave Sleep) — Repair Phase",
  "definition": "Sleep stage N3 characterised by delta waves. Primary tissue repair and hormone secretion phase.",
  "key_events": [
    "Growth hormone (GH) secreted in pulses — largest pulse within first 90 minutes of sleep",
    "Cell autophagy peaks — damaged proteins cleared",
    "Cortisol at its lowest",
    "Immune cytokine repair",
    "Tissue regeneration (skin, muscle, hair follicle support)"
  ],
  "hair_mechanism": "GH → liver → IGF-1 → dermal papilla → anagen promotion (ref: HOR_IGF1_001, BIO_DERMALPAPILLA_001)",
  "depletion_causes": ["Alcohol disrupts N3", "Sleep apnoea fragments N3", "Stimulants delay N3 entry", "Blue light delays sleep onset, reduces N3"]
}
```

---

## 09_STRESS

```json
{
  "id": "STR_ACUTE_001",
  "node_type": "stress",
  "version": "1.0",
  "type": "Acute Stress",
  "definition": "Short-term stress response: fight-or-flight activation via sympathetic nervous system.",
  "hormones_involved": ["HOR_ADRENALINE_001", "HOR_CORTISOL_001"],
  "biological_effects": "Increased heart rate, glucose release, blood flow to muscles. Adaptive response.",
  "hair_impact": "Minimal. Acute stress can trigger telogen effluvium 2–3 months later if severe."
}

{
  "id": "STR_CHRONIC_001",
  "node_type": "stress",
  "version": "1.0",
  "type": "Chronic Stress",
  "definition": "Prolonged psychological or physiological stress with sustained cortisol elevation.",
  "causes": ["Work pressure", "Relationship conflict", "Financial stress", "Chronic illness", "Caregiver burden"],
  "biological_cascade": [
    "CRH → ACTH → Cortisol chronically elevated",
    "Cortisol suppresses HPG axis → disrupts reproductive hormones",
    "Cortisol degrades gut lining → dysbiosis, leaky gut",
    "Cortisol suppresses melatonin → poor sleep",
    "Cortisol increases insulin resistance"
  ],
  "downstream_effects": {
    "hair": "Prolongs telogen → diffuse shedding (ref: HOR_CORTISOL_001)",
    "gut": "GUT_DYSBIOSIS_001, GUT_LEAKYGUT_001",
    "hormones": "HOR_ESTROGEN_001, HOR_THYROID_001 disruption",
    "sleep": "SLP_CIRCADIAN_001 disruption",
    "inflammation": "INF_CHRONIC_001"
  },
  "lab_markers": ["LAB_MORNING_CORTISOL_001", "LAB_DHEA_001"]
}
```

---

## 10_EXERCISE

```json
{
  "id": "EXE_RESISTANCE_001",
  "node_type": "exercise",
  "version": "1.0",
  "type": "Resistance Training",
  "definition": "Exercise using external load to create muscular tension and metabolic stress.",
  "benefits": {
    "metabolic": "Increases muscle mass → improves insulin sensitivity → reduces insulin resistance (ref: BLD_INSULIN_RESISTANCE_001)",
    "hormonal": "Increases IGF-1 and GH → supports hair follicle anagen (ref: HOR_IGF1_001)",
    "recovery": "Stimulates tissue repair pathways (ref: REC_FOLLICLE_001)"
  },
  "caution": "Overtraining → elevated cortisol → impairs recovery and hair growth"
}

{
  "id": "EXE_AEROBIC_001",
  "node_type": "exercise",
  "version": "1.0",
  "type": "Aerobic / Cardiovascular Exercise",
  "definition": "Sustained rhythmic exercise using large muscle groups at moderate intensity.",
  "benefits": {
    "metabolic": "Improves glucose disposal, reduces insulin resistance",
    "cardiovascular": "Reduces blood pressure, improves lipid profile",
    "stress": "Reduces cortisol chronically, raises endorphins",
    "sleep": "Improves deep sleep quality (ref: SLP_DEEPSLEEP_001)"
  },
  "scalp_benefit": "Improves scalp blood flow → better nutrient delivery to hair follicle"
}
```

---

## 11_RECOVERY

```json
{
  "id": "REC_FOLLICLE_001",
  "node_type": "recovery",
  "version": "1.0",
  "tissue": "Hair Follicle",
  "recovery_biology": "Once nutritional or hormonal root cause is corrected, follicle stem cells in the bulge region are activated. They regenerate the dermal papilla and matrix, re-entering anagen.",
  "timeline": {
    "1_month": "Shedding slows as fewer follicles enter telogen",
    "2_3_months": "New fine vellus-like hairs visible at hairline (baby hairs)",
    "4_6_months": "Terminal hair emerging, volume returning",
    "9_12_months": "Full recovery if root cause resolved"
  },
  "rate_limiting_factor": "The root cause MUST be resolved. Recovery is impossible if deficiency persists.",
  "nutrient_refs": ["NUT_IRON_001", "NUT_PROTEIN_001", "NUT_ZINC_001"],
  "sleep_ref": "SLP_DEEPSLEEP_001"
}

{
  "id": "REC_SKIN_001",
  "node_type": "recovery",
  "version": "1.0",
  "tissue": "Skin",
  "recovery_biology": "Skin epidermis regenerates every 28–40 days. Dermis collagen remodelling takes 3–6 months.",
  "timeline": {
    "2_4_weeks": "Inflammation reduces, new epidermal cells emerge",
    "2_3_months": "Collagen synthesis improving, texture smoother",
    "6_months": "Significant improvement in scars and barrier function"
  },
  "nutrient_refs": ["NUT_VITC_001", "NUT_ZINC_001", "NUT_PROTEIN_001", "NUT_OMEGA3_001"]
}
```

---

## 12_INFLAMMATION

```json
{
  "id": "INF_ACUTE_001",
  "node_type": "inflammation",
  "version": "1.0",
  "type": "Acute Inflammation",
  "definition": "Short-term protective immune response to injury or infection.",
  "mediators": ["Histamine", "Prostaglandins", "Bradykinin", "Cytokines (IL-1, IL-6, TNF-α)"],
  "outcome": "Adaptive — resolves after healing. Necessary for tissue repair.",
  "hair_impact": "Acute folliculitis can trigger localised hair loss. Generally reversible."
}

{
  "id": "INF_CHRONIC_001",
  "node_type": "inflammation",
  "version": "1.0",
  "type": "Chronic Low-Grade Inflammation",
  "definition": "Persistent low-level systemic inflammation driven by ongoing stimuli without resolution.",
  "causes": [
    "Gut dysbiosis and leaky gut (LPS → TLR4 activation) — ref: GUT_LEAKYGUT_001",
    "Chronic stress — ref: STR_CHRONIC_001",
    "Poor diet (high omega-6, trans fats, refined sugar)",
    "Visceral obesity (adipose tissue secretes pro-inflammatory adipokines)",
    "Environmental toxins — ref: ENV_POLLUTION_001",
    "Oxidative stress — ref: OXI_FREE_RADICAL_001"
  ],
  "biological_effects": {
    "hair": "Inflammatory cytokines (IL-1, TNF-α) inhibit anagen and induce follicle apoptosis",
    "skin": "Acne, rosacea, eczema, psoriasis flares",
    "hormonal": "Disrupts thyroid function, increases cortisol",
    "metabolic": "Accelerates insulin resistance"
  },
  "markers": ["LAB_CRP_001", "LAB_ESR_001", "LAB_IL6_001"],
  "anti_inflammatory_refs": ["NUT_OMEGA3_001", "NUT_VITD_001", "EXE_AEROBIC_001"]
}
```

---

## 13_OXIDATIVE_STRESS

```json
{
  "id": "OXI_FREE_RADICAL_001",
  "node_type": "oxidative_stress",
  "version": "1.0",
  "topic": "Free Radicals and Oxidative Stress",
  "definition": "Imbalance between reactive oxygen species (ROS) production and antioxidant defence capacity.",
  "sources_of_ROS": ["Mitochondrial ATP production", "UV exposure", "Pollution", "Smoking", "Chronic inflammation", "High blood sugar"],
  "biological_damage": {
    "hair": "Oxidative damage to hair follicle DNA and proteins → premature ageing of follicle → early canities (greying) and shedding",
    "skin": "Collagen and elastin degradation → wrinkles, pigmentation",
    "DNA": "Somatic mutations, accelerated aging"
  },
  "antioxidant_defence": {
    "enzymatic": ["Superoxide dismutase (SOD) — copper, zinc, manganese dependent", "Glutathione peroxidase — selenium dependent (ref: NUT_SELENIUM_001)", "Catalase"],
    "dietary": ["NUT_VITC_001", "NUT_VITD_001", "NUT_OMEGA3_001", "Polyphenols from plants"]
  }
}
```

---

## 14_BLOOD_SUGAR

```json
{
  "id": "BLD_INSULIN_RESISTANCE_001",
  "node_type": "blood_sugar",
  "version": "1.0",
  "condition": "Insulin Resistance",
  "definition": "Reduced cellular sensitivity to insulin, requiring compensatory higher insulin secretion to maintain euglycaemia.",
  "causes": ["High glycaemic diet", "Physical inactivity", "Visceral obesity", "Chronic stress", "Sleep deprivation", "Genetic predisposition"],
  "biological_cascade": [
    "Cells resist insulin → pancreas secretes more insulin",
    "Hyperinsulinemia → stimulates ovarian androgen production",
    "High insulin → IGF-1 elevation → sebum overproduction",
    "Fat cells release inflammatory adipokines → INF_CHRONIC_001"
  ],
  "downstream_effects": {
    "hormonal": "HOR_DHT_001 elevation via androgen pathway",
    "skin": "Acne, skin tags, acanthosis nigricans",
    "hair": "Androgenic hair loss via DHT elevation",
    "weight": "Progressive weight gain, visceral fat accumulation"
  },
  "lab_markers": ["LAB_FASTING_INSULIN_001", "LAB_HOMA_IR_001", "LAB_HBA1C_001", "LAB_FASTING_GLUCOSE_001"]
}

{
  "id": "BLD_PREDIABETES_001",
  "node_type": "blood_sugar",
  "version": "1.0",
  "condition": "Prediabetes",
  "definition": "Fasting glucose 100–125 mg/dL or HbA1c 5.7–6.4%. Reversible with lifestyle intervention.",
  "indian_risk_note": "Indians develop insulin resistance and diabetes at lower BMI than Western populations. Asian-specific cut-offs apply.",
  "lab_markers": ["LAB_FASTING_GLUCOSE_001", "LAB_HBA1C_001", "LAB_FASTING_INSULIN_001"]
}
```

---

## 15_HYDRATION

```json
{
  "id": "HYD_FLUID_001",
  "node_type": "hydration",
  "version": "1.0",
  "topic": "Fluid Balance and Hydration",
  "optimal_intake": "30–35 mL per kg body weight per day. More in heat/exercise.",
  "electrolytes": ["Sodium", "Potassium", "Magnesium (ref: NUT_MAGNESIUM_001)", "Chloride"],
  "skin_hydration": "Adequate water and essential fatty acids (ref: NUT_OMEGA3_001) maintain skin barrier moisture.",
  "hair_connection": "Dehydration → reduced scalp blood flow → less nutrient delivery to follicle",
  "cellular_hydration": "Intracellular hydration depends on electrolyte balance, not just water intake."
}
```

---

## 16_ENVIRONMENT

```json
{
  "id": "ENV_HARDWATER_001",
  "node_type": "environment",
  "version": "1.0",
  "stressor": "Hard Water",
  "definition": "Water with high calcium and magnesium mineral content (>120 ppm total hardness).",
  "hair_effects": "Calcium and magnesium deposits coat hair shaft → reduced elasticity, increased friction, breakage, scalp irritation. Does NOT cause follicle-level hair loss.",
  "important_note": "Hard water damages the hair shaft (cosmetic issue). It does NOT damage the follicle or cause systemic hair loss. Confounded frequently with nutritional causes.",
  "prevalence": "Common in North and West India (Delhi, Mumbai, Rajasthan water supplies)"
}

{
  "id": "ENV_UV_001",
  "node_type": "environment",
  "version": "1.0",
  "stressor": "UV Exposure",
  "definition": "Ultraviolet radiation from sunlight.",
  "positive_effects": "UVB → Vitamin D synthesis (ref: NUT_VITD_001)",
  "negative_effects": {
    "skin": "UV-A → collagen degradation (photoaging). UV-B → DNA damage → skin cancer risk",
    "hair": "UV-B → oxidative damage to hair proteins, cuticle weakening → colour fading, brittleness"
  }
}

{
  "id": "ENV_POLLUTION_001",
  "node_type": "environment",
  "version": "1.0",
  "stressor": "Air Pollution",
  "definition": "Particulate matter (PM2.5, PM10) and gaseous pollutants.",
  "hair_effects": "Scalp deposits from PM2.5 → oxidative stress in follicle → inflammation → premature telogen. Strongly linked to urban hair loss patterns.",
  "skin_effects": "Reactive oxygen species from pollution → accelerated skin aging, acne, pigmentation"
}
```

---

## 17_MEDICAL_CONDITIONS

```json
{
  "id": "MED_PCOS_001",
  "node_type": "medical_condition",
  "version": "1.0",
  "name": "Polycystic Ovarian Syndrome (PCOS)",
  "definition": "Common endocrine disorder characterised by hormonal imbalance, ovarian dysfunction, and metabolic disruption.",
  "diagnostic_criteria": "Rotterdam Criteria: 2 of 3 — irregular periods, androgen excess (clinical or biochemical), polycystic ovaries on ultrasound.",
  "root_mechanisms": [
    "Insulin resistance → hyperinsulinemia → stimulates ovarian androgen production",
    "LH:FSH ratio imbalance → anovulation",
    "Chronic low-grade inflammation"
  ],
  "symptom_refs": ["SYM_HAIRFALL_001", "SYM_ACNE_001", "SYM_WEIGHTGAIN_001", "SYM_IRREGULARPERIODS_001"],
  "lab_markers": ["LAB_LH_FSH_RATIO_001", "LAB_FREE_TESTOSTERONE_001", "LAB_FASTING_INSULIN_001", "LAB_DHEAS_001"],
  "hormone_refs": ["HOR_INSULIN_001", "HOR_DHT_001", "HOR_LH_001"],
  "pathway_ref": "PATH_PCOS_HAIR_001",
  "prevalence_india": "~22–25% of reproductive-age Indian women"
}

{
  "id": "MED_HYPOTHYROID_001",
  "node_type": "medical_condition",
  "version": "1.0",
  "name": "Hypothyroidism",
  "definition": "Underactive thyroid gland producing insufficient thyroid hormone.",
  "types": ["Primary (Hashimoto's autoimmune)", "Secondary (pituitary failure)", "Iodine deficiency induced"],
  "symptom_refs": ["SYM_HAIRFALL_001", "SYM_FATIGUE_001", "SYM_WEIGHTGAIN_001", "SYM_DRYSKIN_001", "SYM_BRAINFOG_001"],
  "lab_markers": ["LAB_TSH_001", "LAB_FT3_001", "LAB_FT4_001", "LAB_ANTI_TPO_001"],
  "hormone_ref": "HOR_THYROID_001",
  "pathway_ref": "PATH_THYROID_HAIR_001",
  "prevalence_india": "~10.95% of Indian population have thyroid dysfunction"
}

{
  "id": "MED_ANEMIA_001",
  "node_type": "medical_condition",
  "version": "1.0",
  "name": "Iron Deficiency Anaemia",
  "definition": "Haemoglobin below 12 g/dL (women) or 13.5 g/dL (men) with iron deficiency as cause.",
  "stages": [
    "Stage 1: Iron stores depleted (low ferritin, normal Hb)",
    "Stage 2: Iron-deficient erythropoiesis (low ferritin, reduced TIBC saturation)",
    "Stage 3: Iron deficiency anaemia (low Hb)"
  ],
  "hair_note": "Hair loss begins at Stage 1 (low ferritin alone). Does NOT require anaemia to impair hair growth.",
  "prevalence_india": "~59% of Indian women aged 15–49 are anaemic (NFHS-5 data)",
  "lab_markers": ["LAB_FERRITIN_001", "LAB_HB_001", "LAB_MCV_001", "LAB_SERUM_IRON_001"],
  "pathway_ref": "PATH_IRON_HAIR_001"
}
```

---

## 18_MEDICATIONS

```json
{
  "id": "MEDS_PPIS_001",
  "node_type": "medication",
  "version": "1.0",
  "name": "Proton Pump Inhibitors (PPIs)",
  "examples": ["Omeprazole", "Pantoprazole", "Rabeprazole"],
  "mechanism": "Suppress gastric acid by blocking H+/K+ ATPase pump",
  "side_effects": {
    "nutrient_depletion": ["NUT_B12_001 (impaired IF-dependent absorption)", "NUT_IRON_001 (requires acid for non-heme)", "NUT_MAGNESIUM_001"],
    "hair_effect": "Chronic use → B12 and iron depletion → hair loss"
  },
  "prevalence": "Commonly used for acidity — very prevalent in India without monitoring"
}

{
  "id": "MEDS_METFORMIN_001",
  "node_type": "medication",
  "version": "1.0",
  "name": "Metformin",
  "indication": "Type 2 diabetes, PCOS",
  "mechanism": "Reduces hepatic glucose production, improves insulin sensitivity",
  "side_effects": {
    "nutrient_depletion": ["NUT_B12_001 — impairs ileal absorption"],
    "hair_effect": "B12 depletion over years → hair loss, fatigue"
  },
  "monitoring": "Check B12 annually in Metformin users (ref: LAB_B12_001)"
}

{
  "id": "MEDS_OCP_001",
  "node_type": "medication",
  "version": "1.0",
  "name": "Oral Contraceptive Pills (OCPs)",
  "mechanism": "Synthetic estrogen and progestogen suppress ovulation",
  "hair_effects": {
    "on_pill": "Some progestins with high androgenic activity → telogen effluvium",
    "post_pill": "Post-OCP telogen effluvium — shedding 2–3 months after stopping pill as estrogen drops"
  },
  "nutrient_depletion": ["NUT_B12_001", "NUT_VITC_001", "NUT_MAGNESIUM_001", "NUT_ZINC_001"]
}
```

---

## 19_GENETICS

```json
{
  "id": "GEN_ANDROGEN_SENSITIVITY_001",
  "node_type": "genetics",
  "version": "1.0",
  "topic": "Androgen Receptor Sensitivity",
  "definition": "Genetic variation in androgen receptor (AR) gene affecting how strongly DHT binds to receptors in hair follicles.",
  "inheritance": "X-linked (maternal inheritance pattern for pattern baldness)",
  "clinical_implication": "High AR sensitivity → normal DHT levels still cause follicle miniaturisation",
  "assessment": "Family history of androgenetic alopecia (father, maternal grandfather)",
  "related_hormone": "HOR_DHT_001"
}

{
  "id": "GEN_MTHFR_001",
  "node_type": "genetics",
  "version": "1.0",
  "topic": "MTHFR Gene Variant",
  "definition": "Methylenetetrahydrofolate reductase gene variant C677T or A1298C affecting folate metabolism.",
  "clinical_implication": "Impaired folate and B12 methylation → elevated homocysteine → cardiovascular risk, impaired DNA synthesis",
  "nutrient_refs": ["NUT_B12_001", "NUT_FOLATE_001"],
  "lab_marker": "LAB_HOMOCYSTEINE_001"
}

{
  "id": "GEN_THYROID_AUTOIMMUNE_001",
  "node_type": "genetics",
  "version": "1.0",
  "topic": "Thyroid Autoimmune Predisposition",
  "definition": "HLA gene variants increasing risk of Hashimoto's thyroiditis and Graves' disease.",
  "clinical_implication": "Family history of thyroid disease → higher priority screening (ref: LAB_TSH_001, LAB_ANTI_TPO_001)"
}
```

---

## 20_LIFE_STAGES

```json
{
  "id": "LIF_PREGNANCY_001",
  "node_type": "life_stage",
  "version": "1.0",
  "stage": "Pregnancy",
  "hormonal_profile": "Estrogen and progesterone peak → prolongs anagen → thick hair during pregnancy",
  "nutritional_demands": ["NUT_IRON_001 (27 mg/day)", "NUT_FOLATE_001", "NUT_B12_001", "NUT_VITD_001"],
  "risks": "Iron deficiency very common in Indian pregnant women",
  "lab_monitoring": ["LAB_FERRITIN_001", "LAB_HB_001", "LAB_VITD_001", "LAB_TSH_001"]
}

{
  "id": "LIF_POSTPARTUM_001",
  "node_type": "life_stage",
  "version": "1.0",
  "stage": "Postpartum (0–6 months after delivery)",
  "hair_mechanism": "Estrogen drops sharply after delivery → all hairs that were held in anagen enter telogen simultaneously → massive shedding at 2–4 months postpartum (postpartum telogen effluvium — NORMAL physiological response)",
  "important_note": "Postpartum hair loss is NORMAL and self-limiting. Distinguish from iron deficiency (check ferritin — common concurrent cause).",
  "nutritional_risks": ["Iron depletion from delivery blood loss", "B12 if breastfeeding", "Vitamin D"],
  "recovery_timeline": "Hair fully recovers by 9–12 months postpartum if nutrition is adequate."
}

{
  "id": "LIF_MENOPAUSE_001",
  "node_type": "life_stage",
  "version": "1.0",
  "stage": "Menopause",
  "definition": "12 consecutive months without menstruation. Average age in India: 46–47 years.",
  "hormonal_profile": "Estrogen and progesterone decline. Androgen-to-estrogen ratio shifts → relative androgen excess.",
  "hair_effects": "Female pattern hair loss (FPHL) — diffuse crown thinning, preserved hairline. Estrogen loss removes anagen-prolonging protection.",
  "other_effects": ["Skin thinning and dryness", "Bone density loss", "Vasomotor symptoms"],
  "lab_monitoring": ["LAB_FSH_001", "LAB_ESTRADIOL_001", "LAB_VITD_001", "LAB_FERRITIN_001"]
}

{
  "id": "LIF_ADOLESCENCE_001",
  "node_type": "life_stage",
  "version": "1.0",
  "stage": "Adolescence (13–18 years)",
  "hormonal_shifts": "Androgen surge in both sexes. IGF-1 peaks.",
  "hair_risks": "Acne and oiliness common due to androgen-driven sebum. PCOS often first manifests.",
  "nutritional_risks": "Iron deficiency after menarche onset. Protein inadequacy with poor diet."
}

{
  "id": "LIF_AGING_001",
  "node_type": "life_stage",
  "version": "1.0",
  "stage": "Aging (50+)",
  "biological_changes": ["Collagen production declines ~1% per year after 30", "IGF-1 declines", "NAD+ declines → mitochondrial efficiency drops", "Stem cell activity in follicle bulge reduces"],
  "hair_effects": "Follicle miniaturisation, slower growth rate, grey hair from melanocyte depletion",
  "intervention_opportunity": "Protein, Vitamin D, resistance training, and sleep optimisation significantly offset aging effects."
}
```

---

## 21_FOOD_DATABASE

**India-first. Affordable. Regional. Accurate nutrient values.**

```json
{
  "id": "FOD_SPINACH_001",
  "node_type": "food",
  "version": "1.0",
  "name": "Palak (Spinach)",
  "category": "green_leafy_vegetable",
  "regional_availability": "Pan-India, affordable, year-round",
  "nutrients_per_100g_raw": {
    "iron_mg": 2.7,
    "vitamin_c_mg": 28,
    "folate_mcg": 194,
    "magnesium_mg": 79,
    "vitamin_a_mcg": 469
  },
  "absorption_tip": "Cook with lemon juice or tomato (Vitamin C enhances iron absorption). Avoid with chai.",
  "nutrient_refs": ["NUT_IRON_001", "NUT_VITC_001", "NUT_MAGNESIUM_001"],
  "cost_rating": "low",
  "cooking_methods": ["Sauté (retain more nutrients)", "Curry", "Dal palak"]
}

{
  "id": "FOD_RAJMA_001",
  "node_type": "food",
  "version": "1.0",
  "name": "Rajma (Kidney Beans)",
  "category": "legume",
  "regional_availability": "North India staple, available Pan-India",
  "nutrients_per_100g_cooked": {
    "iron_mg": 8.2,
    "protein_g": 8.7,
    "zinc_mg": 1.1,
    "folate_mcg": 130,
    "fibre_g": 6.4
  },
  "absorption_tip": "Soak overnight and discard water. Pressure cook. Eat with lemon-based chaas for Vitamin C.",
  "phytate_note": "Overnight soaking reduces phytates by 30–40%, improving iron and zinc bioavailability.",
  "nutrient_refs": ["NUT_IRON_001", "NUT_PROTEIN_001", "NUT_ZINC_001"],
  "cost_rating": "low"
}

{
  "id": "FOD_JAGGERY_001",
  "node_type": "food",
  "version": "1.0",
  "name": "Jaggery (Gur)",
  "category": "sweetener_iron_source",
  "regional_availability": "Pan-India. Village and urban markets.",
  "nutrients_per_100g": {
    "iron_mg": 11.0,
    "calcium_mg": 80,
    "potassium_mg": 1056
  },
  "practical_tip": "Replace refined sugar with jaggery in chai. Better nutritional profile.",
  "caution": "High glycaemic — limit quantity in insulin-resistant individuals",
  "nutrient_refs": ["NUT_IRON_001"],
  "cost_rating": "low"
}

{
  "id": "FOD_AMLA_001",
  "node_type": "food",
  "version": "1.0",
  "name": "Amla (Indian Gooseberry)",
  "category": "fruit_vitamin_c_source",
  "regional_availability": "Pan-India. Dried amla available year-round.",
  "nutrients_per_100g_raw": {
    "vitamin_c_mg": 600,
    "iron_mg": 1.2,
    "antioxidants": "Gallic acid, ellagic acid"
  },
  "hair_benefit": "Vitamin C → iron absorption enhancer (ref: ABS_IRON_001). Antioxidants protect follicle from oxidative damage.",
  "practical_tip": "1 amla/day with breakfast. Dried amla powder in warm water is practical.",
  "nutrient_refs": ["NUT_VITC_001", "NUT_IRON_001"],
  "cost_rating": "low"
}

{
  "id": "FOD_SESAME_001",
  "node_type": "food",
  "version": "1.0",
  "name": "Til (Sesame Seeds)",
  "category": "seeds",
  "regional_availability": "Pan-India. Common in chikkis, laddoos, chutneys.",
  "nutrients_per_100g": {
    "iron_mg": 14.6,
    "calcium_mg": 975,
    "zinc_mg": 7.8,
    "protein_g": 17.7,
    "magnesium_mg": 351
  },
  "practical_tip": "Add to salads, chutneys, or consume as til laddoo. Roasting improves palatability.",
  "nutrient_refs": ["NUT_IRON_001", "NUT_ZINC_001", "NUT_MAGNESIUM_001", "NUT_PROTEIN_001"],
  "cost_rating": "low"
}

{
  "id": "FOD_PUMPKIN_SEEDS_001",
  "node_type": "food",
  "version": "1.0",
  "name": "Kaddu ke Beej (Pumpkin Seeds)",
  "category": "seeds",
  "nutrients_per_100g": {
    "zinc_mg": 7.8,
    "magnesium_mg": 592,
    "iron_mg": 8.8,
    "protein_g": 19.4,
    "omega3_g": 0.1
  },
  "hair_benefit": "High zinc → DHT inhibition (ref: NUT_ZINC_001). Magnesium → cortisol regulation.",
  "practical_tip": "30g/day as snack. Roast with black salt.",
  "nutrient_refs": ["NUT_ZINC_001", "NUT_MAGNESIUM_001", "NUT_IRON_001"],
  "cost_rating": "medium"
}

{
  "id": "FOD_DAL_001",
  "node_type": "food",
  "version": "1.0",
  "name": "Dal (Lentils — Mixed)",
  "category": "legume",
  "varieties": ["Masoor (red lentil)", "Moong", "Toor", "Urad", "Chana dal"],
  "nutrients_per_100g_cooked": {
    "protein_g": 9.0,
    "iron_mg": 3.3,
    "folate_mcg": 181,
    "fibre_g": 7.9
  },
  "practical_tip": "Dal-rice combination provides complete amino acid profile (complementary proteins).",
  "cost_rating": "low",
  "nutrient_refs": ["NUT_PROTEIN_001", "NUT_IRON_001"]
}
```

---

## 22_LAB_MARKERS

```json
{
  "id": "LAB_FERRITIN_001",
  "node_type": "lab_marker",
  "version": "1.0",
  "name": "Serum Ferritin",
  "measures": "Iron storage protein — the most sensitive indicator of iron stores",
  "ranges": {
    "standard_lab_normal": "12–150 ng/mL",
    "functional_health": "50–150 ng/mL",
    "hair_specific": "70–150 ng/mL (below 70 → hair loss risk even without anaemia)",
    "deficient": "Below 30 ng/mL",
    "critically_low": "Below 12 ng/mL"
  },
  "confounders": "Ferritin is an acute-phase reactant — can be falsely NORMAL or HIGH during inflammation/infection. Always check CRP alongside.",
  "action_triggers": {
    "below_30": "Begin dietary iron intervention immediately",
    "below_70": "Optimise iron-rich diet, check absorption blockers",
    "below_12": "Medical referral — risk of anaemia"
  },
  "nutrition_ref": "NUT_IRON_001",
  "symptom_refs": ["SYM_HAIRFALL_001", "SYM_FATIGUE_001"],
  "test_frequency": "Every 3 months during active intervention",
  "cost_india": "₹300–600"
}

{
  "id": "LAB_TSH_001",
  "node_type": "lab_marker",
  "version": "1.0",
  "name": "Thyroid Stimulating Hormone (TSH)",
  "measures": "Pituitary signal to thyroid — primary thyroid screening test",
  "ranges": {
    "standard_normal": "0.4–4.0 mIU/L",
    "functional_optimal": "1.0–2.5 mIU/L",
    "subclinical_hypothyroid": "4.0–10.0 mIU/L with normal FT4",
    "overt_hypothyroid": "Above 10.0 mIU/L"
  },
  "confounders": "TSH alone can miss subclinical dysfunction. Always pair with FT3, FT4.",
  "hormone_ref": "HOR_THYROID_001",
  "cost_india": "₹200–400"
}

{
  "id": "LAB_VITD_001",
  "node_type": "lab_marker",
  "version": "1.0",
  "name": "25-Hydroxy Vitamin D",
  "measures": "Vitamin D storage form — best indicator of Vitamin D status",
  "ranges": {
    "deficient": "Below 20 ng/mL",
    "insufficient": "20–30 ng/mL",
    "sufficient": "30–60 ng/mL",
    "optimal_hair_immune": "50–80 ng/mL"
  },
  "indian_note": "Paradox — high sun exposure country with endemic deficiency due to indoor lifestyle, dark skin, clothing coverage, and vegetarian diet.",
  "prevalence_india": "~70–90% of Indian population is insufficient or deficient",
  "nutrition_ref": "NUT_VITD_001",
  "cost_india": "₹600–1200"
}

{
  "id": "LAB_B12_001",
  "node_type": "lab_marker",
  "version": "1.0",
  "name": "Serum Vitamin B12",
  "measures": "Circulating B12 levels",
  "ranges": {
    "standard_deficient": "Below 200 pg/mL",
    "functional_deficient": "Below 400 pg/mL",
    "optimal": "400–900 pg/mL"
  },
  "confounders": "Serum B12 can be falsely normal in functional deficiency. Check MCV and homocysteine for confirmation.",
  "nutrition_ref": "NUT_B12_001",
  "cost_india": "₹400–700"
}

{
  "id": "LAB_HBA1C_001",
  "node_type": "lab_marker",
  "version": "1.0",
  "name": "HbA1c (Glycated Haemoglobin)",
  "measures": "Average blood glucose over 2–3 months",
  "ranges": {
    "normal": "Below 5.7%",
    "prediabetes": "5.7–6.4%",
    "diabetes": "6.5% and above",
    "treatment_target": "Below 7.0% for most diabetics"
  },
  "blood_sugar_ref": "BLD_INSULIN_RESISTANCE_001",
  "cost_india": "₹300–500"
}

{
  "id": "LAB_FASTING_INSULIN_001",
  "node_type": "lab_marker",
  "version": "1.0",
  "name": "Fasting Insulin",
  "measures": "Baseline insulin level — indicator of insulin resistance",
  "ranges": {
    "normal": "2–10 μIU/mL",
    "borderline": "10–15 μIU/mL",
    "insulin_resistant": "Above 15 μIU/mL"
  },
  "homa_ir": "HOMA-IR = (Fasting Glucose × Fasting Insulin) / 405. Above 2.5 = insulin resistant.",
  "hormone_ref": "HOR_INSULIN_001",
  "cost_india": "₹400–700",
  "note": "Rarely tested in India. Critical for PCOS and metabolic assessment."
}

{
  "id": "LAB_CRP_001",
  "node_type": "lab_marker",
  "version": "1.0",
  "name": "High-sensitivity CRP (hs-CRP)",
  "measures": "Systemic inflammation marker",
  "ranges": {
    "low_risk": "Below 1 mg/L",
    "moderate_risk": "1–3 mg/L",
    "high_risk": "Above 3 mg/L",
    "acute_infection": "Above 10 mg/L — not interpretable for chronic inflammation"
  },
  "use_in_healthsync": "Required to validate ferritin result. Elevated CRP invalidates ferritin as iron marker.",
  "inflammation_ref": "INF_CHRONIC_001",
  "cost_india": "₹400–800"
}
```

---

---

# LAYER 1.5 — PATHWAYS

## 23_PATHWAYS

**Purpose:** Named biological chains that trace root cause to symptom through cellular steps. Each pathway is the explicit logic the AI follows. Prevents hallucination by forcing reference-based reasoning. No intervention fires without a pathway.

```json
{
  "id": "PATH_IRON_HAIR_001",
  "node_type": "pathway",
  "version": "1.0",
  "name": "Iron Deficiency → Hair Loss Pathway",
  "root_cause": "Iron deficiency / low ferritin",
  "terminal_symptom": "SYM_HAIRFALL_001",
  "confidence_base": 0.72,
  "prevalence_india": "Most common cause of hair loss in Indian women aged 15–45",
  "biological_chain": [
    {
      "step": 1,
      "node_ref": "NUT_IRON_001",
      "event": "Serum ferritin drops below 70 ng/mL",
      "mechanism": "Iron stores insufficient to support high-turnover tissues"
    },
    {
      "step": 2,
      "node_ref": "BIO_MATRIX_001",
      "event": "Ribonucleotide reductase activity reduces — DNA synthesis in matrix cells slows",
      "mechanism": "Iron is essential cofactor for this rate-limiting enzyme"
    },
    {
      "step": 3,
      "node_ref": "BIO_FOLLICLE_001",
      "event": "Anagen phase shortens — follicle enters telogen prematurely",
      "mechanism": "Insufficient matrix cell division cannot sustain full anagen duration"
    },
    {
      "step": 4,
      "node_ref": "SYM_HAIRFALL_001",
      "event": "Diffuse hair shedding — 150–300+ hairs per day",
      "mechanism": "Elevated telogen-to-anagen ratio → mass shedding"
    }
  ],
  "amplifying_factors": [
    { "factor": "ABS_IRON_001", "description": "Poor absorption (tea with meals, no Vitamin C)" },
    { "factor": "GUT_MALABSORPTION_001", "description": "Dysbiosis or H. pylori impairs iron uptake" },
    { "factor": "LIF_PREGNANCY_001", "description": "Pregnancy dramatically increases iron demand" },
    { "factor": "MED_ANEMIA_001", "description": "Heavy menstrual blood loss exceeds intake" }
  ],
  "lab_confirmation": ["LAB_FERRITIN_001", "LAB_SERUM_IRON_001", "LAB_CBC_001", "LAB_CRP_001"],
  "intervention_ref": "INT_IRON_001",
  "distinguishing_from": {
    "PATH_DHT_HAIR_001": "Iron → diffuse all-over. DHT → temples/crown pattern.",
    "PATH_THYROID_HAIR_001": "Thyroid → check FT3/FT4/TSH. Often concurrent with iron."
  }
}

{
  "id": "PATH_DHT_HAIR_001",
  "node_type": "pathway",
  "version": "1.0",
  "name": "DHT Excess → Androgenetic Alopecia Pathway",
  "root_cause": "Androgen excess or androgen receptor hypersensitivity",
  "terminal_symptom": "SYM_HAIRTHIN_001",
  "confidence_base": 0.65,
  "biological_chain": [
    {
      "step": 1,
      "node_ref": "HOR_DHT_001",
      "event": "DHT production elevated or AR sensitivity high",
      "mechanism": "Testosterone → 5-alpha reductase → DHT. Excess from insulin resistance or genetic AR sensitivity."
    },
    {
      "step": 2,
      "node_ref": "BIO_DERMALPAPILLA_001",
      "event": "DHT binds androgen receptors in dermal papilla",
      "mechanism": "Activates TGF-β2 pathway, inhibits Wnt/β-catenin signalling"
    },
    {
      "step": 3,
      "node_ref": "BIO_FOLLICLE_001",
      "event": "Follicle progressively miniaturises over cycles",
      "mechanism": "Each anagen cycle produces finer, shorter hair until vellus-like"
    },
    {
      "step": 4,
      "node_ref": "SYM_HAIRTHIN_001",
      "event": "Progressive thinning at crown/temples (females) or Norwood pattern (males)",
      "mechanism": "Miniaturised terminal follicles produce vellus hairs only"
    }
  ],
  "amplifying_factors": [
    { "factor": "BLD_INSULIN_RESISTANCE_001", "description": "Hyperinsulinemia stimulates ovarian androgen production" },
    { "factor": "GEN_ANDROGEN_SENSITIVITY_001", "description": "Genetic AR hypersensitivity" },
    { "factor": "MED_PCOS_001", "description": "PCOS is primary androgen excess cause in women" }
  ],
  "lab_confirmation": ["LAB_FREE_TESTOSTERONE_001", "LAB_SHBG_001", "LAB_DHEAS_001", "LAB_FASTING_INSULIN_001"],
  "intervention_ref": "INT_DHT_001",
  "distinguishing_from": {
    "PATH_IRON_HAIR_001": "DHT → patterned recession. Iron → diffuse all-scalp.",
    "PATH_THYROID_HAIR_001": "Thyroid → systemic symptoms. DHT → primarily cosmetic."
  }
}

{
  "id": "PATH_THYROID_HAIR_001",
  "node_type": "pathway",
  "version": "1.0",
  "name": "Hypothyroidism → Hair Loss Pathway",
  "root_cause": "Insufficient active thyroid hormone (T3)",
  "terminal_symptom": "SYM_HAIRFALL_001",
  "confidence_base": 0.60,
  "biological_chain": [
    {
      "step": 1,
      "node_ref": "HOR_THYROID_001",
      "event": "T3 (active thyroid hormone) insufficient — TSH elevated",
      "mechanism": "Autoimmune (Hashimoto's), iodine/selenium deficiency, or pituitary failure"
    },
    {
      "step": 2,
      "node_ref": "BIO_FOLLICLE_001",
      "event": "Follicle cell metabolism slows — anagen phase shortens",
      "mechanism": "T3 receptors in follicle regulate metabolic rate of matrix cells. Low T3 → slow division."
    },
    {
      "step": 3,
      "node_ref": "BIO_MATRIX_001",
      "event": "Reduced protein synthesis in hair shaft",
      "mechanism": "Thyroid hormone regulates keratin gene expression"
    },
    {
      "step": 4,
      "node_ref": "SYM_HAIRFALL_001",
      "event": "Diffuse hair loss, brittle texture, outer third of eyebrows thinning",
      "mechanism": "Shortened anagen + reduced keratin quality"
    }
  ],
  "amplifying_factors": [
    { "factor": "NUT_SELENIUM_001", "description": "Selenium deficiency impairs T4→T3 conversion" },
    { "factor": "NUT_IRON_001", "description": "Iron deficiency impairs thyroid peroxidase enzyme — reduces T4 synthesis" },
    { "factor": "INF_CHRONIC_001", "description": "Inflammation suppresses deiodinase enzymes → low T3 despite normal TSH" }
  ],
  "hallmark_symptoms": ["Fatigue + cold intolerance + weight gain + constipation + hair loss = strong thyroid signal"],
  "lab_confirmation": ["LAB_TSH_001", "LAB_FT3_001", "LAB_FT4_001", "LAB_ANTI_TPO_001"],
  "intervention_ref": "INT_THYROID_001"
}

{
  "id": "PATH_PCOS_HAIR_001",
  "node_type": "pathway",
  "version": "1.0",
  "name": "PCOS → Hair Loss Pathway",
  "root_cause": "Polycystic Ovarian Syndrome — insulin resistance + androgen excess",
  "terminal_symptoms": ["SYM_HAIRFALL_001", "SYM_ACNE_001", "SYM_IRREGULARPERIODS_001"],
  "confidence_base": 0.75,
  "biological_chain": [
    {
      "step": 1,
      "node_ref": "BLD_INSULIN_RESISTANCE_001",
      "event": "Insulin resistance → compensatory hyperinsulinemia",
      "mechanism": "High sugar diet, sedentary lifestyle, genetic predisposition"
    },
    {
      "step": 2,
      "node_ref": "HOR_INSULIN_001",
      "event": "Hyperinsulinemia stimulates ovarian theca cells to produce androgens",
      "mechanism": "Insulin → LH receptor sensitisation → androstenedione and testosterone overproduction"
    },
    {
      "step": 3,
      "node_ref": "HOR_DHT_001",
      "event": "Elevated testosterone converts to DHT",
      "mechanism": "5-alpha reductase converts excess testosterone → elevated DHT"
    },
    {
      "step": 4,
      "node_ref": "BIO_DERMALPAPILLA_001",
      "event": "DHT miniaturises follicles",
      "mechanism": "Same as PATH_DHT_HAIR_001 step 2–3"
    },
    {
      "step": 5,
      "node_ref": "SYM_HAIRFALL_001",
      "event": "Female pattern hair loss + acne + irregular periods cluster",
      "mechanism": "Multi-system androgen excess manifestation"
    }
  ],
  "amplifying_factors": [
    { "factor": "INF_CHRONIC_001", "description": "Chronic inflammation worsens insulin resistance in PCOS" },
    { "factor": "GUT_DYSBIOSIS_001", "description": "Dysbiosis → estrogen recirculation → worsens hormonal imbalance" }
  ],
  "lab_confirmation": [
    "LAB_FREE_TESTOSTERONE_001",
    "LAB_DHEAS_001",
    "LAB_LH_FSH_RATIO_001",
    "LAB_FASTING_INSULIN_001",
    "LAB_HBA1C_001"
  ],
  "intervention_ref": "INT_PCOS_001",
  "distinguishing_cluster": "SCL_PCOS_001"
}

{
  "id": "PATH_CORTISOL_HAIR_001",
  "node_type": "pathway",
  "version": "1.0",
  "name": "Chronic Stress → Cortisol → Hair Loss Pathway",
  "root_cause": "Chronic psychological or physiological stress → sustained cortisol elevation",
  "terminal_symptom": "SYM_HAIRFALL_001",
  "confidence_base": 0.55,
  "biological_chain": [
    {
      "step": 1,
      "node_ref": "STR_CHRONIC_001",
      "event": "Chronic stress activates HPA axis continuously",
      "mechanism": "CRH → ACTH → cortisol — no recovery phase"
    },
    {
      "step": 2,
      "node_ref": "HOR_CORTISOL_001",
      "event": "Elevated cortisol signals follicles to enter telogen",
      "mechanism": "Corticotropin-releasing hormone (CRH) expressed locally in follicle → triggers catagen/telogen"
    },
    {
      "step": 3,
      "node_ref": "BIO_FOLLICLE_001",
      "event": "Mass telogen entry — telogen effluvium",
      "mechanism": "Stress-induced synchronised telogen entry → 2–3 months later, synchronised shedding"
    },
    {
      "step": 4,
      "node_ref": "SYM_HAIRFALL_001",
      "event": "Diffuse shedding 2–3 months after stress onset",
      "mechanism": "Delayed presentation (telogen phase duration) confuses attribution"
    }
  ],
  "amplifying_factors": [
    { "factor": "SLP_DEEPSLEEP_001", "description": "Stress disrupts deep sleep → reduced IGF-1 → double impact on follicle" },
    { "factor": "NUT_MAGNESIUM_001", "description": "Stress depletes magnesium → worsens cortisol dysregulation" }
  ],
  "lab_confirmation": ["LAB_MORNING_CORTISOL_001", "LAB_DHEA_001"],
  "intervention_ref": "INT_STRESS_001"
}

{
  "id": "PATH_GUT_ACNE_001",
  "node_type": "pathway",
  "version": "1.0",
  "name": "Gut Dysbiosis → Systemic Inflammation → Acne Pathway",
  "root_cause": "Gut microbiome imbalance → intestinal permeability → systemic inflammation",
  "terminal_symptom": "SYM_ACNE_001",
  "confidence_base": 0.60,
  "biological_chain": [
    {
      "step": 1,
      "node_ref": "GUT_DYSBIOSIS_001",
      "event": "Microbiome imbalance — beneficial bacteria depleted",
      "mechanism": "Antibiotics, poor diet, stress"
    },
    {
      "step": 2,
      "node_ref": "GUT_LEAKYGUT_001",
      "event": "Tight junctions loosen → LPS enters bloodstream",
      "mechanism": "Lipopolysaccharide (LPS) from gram-negative bacteria triggers TLR4 receptors"
    },
    {
      "step": 3,
      "node_ref": "INF_CHRONIC_001",
      "event": "Systemic low-grade inflammation — IL-1, TNF-α elevated",
      "mechanism": "LPS → NF-κB pathway → inflammatory cytokines"
    },
    {
      "step": 4,
      "node_ref": "BIO_SEBGLAND_001",
      "event": "Inflammation upregulates sebum production and keratinocyte stickiness",
      "mechanism": "IL-1 stimulates sebocytes; TNF-α increases keratinocyte cohesion → pore blockage"
    },
    {
      "step": 5,
      "node_ref": "SYM_ACNE_001",
      "event": "Inflammatory acne — papules, pustules, particularly jawline/cheek",
      "mechanism": "Blocked pore + P. acnes bacterial overgrowth + inflammation = acne lesion"
    }
  ],
  "lab_confirmation": ["LAB_CRP_001"],
  "intervention_ref": "INT_GUT_001"
}
```

---

---

# LAYER 2 — REASONING

---

## 24_AI_QUESTIONS

```json
{
  "id": "AIQ_HAIRFALL_001",
  "node_type": "ai_question_set",
  "version": "1.0",
  "trigger_symptoms": ["SYM_HAIRFALL_001"],
  "purpose": "Narrow root cause probability before loading Decision Engine. Collect minimum necessary data.",
  "questions": [
    {
      "q_id": "AQ001",
      "question": "How long have you been noticing increased hair fall?",
      "type": "single_choice",
      "options": ["Less than 1 month", "1–3 months", "3–6 months", "More than 6 months"],
      "inference": {
        "Less than 1 month": "Acute trigger — stress, illness, medication change. Lower chronic cause probability.",
        "3–6 months": "Nutritional or hormonal. Most common window for iron deficiency presentation.",
        "More than 6 months": "Chronic — androgenetic, thyroid, or long-standing deficiency."
      }
    },
    {
      "q_id": "AQ002",
      "question": "Do you feel unusually tired or low on energy?",
      "type": "boolean",
      "inference": {
        "yes": "+0.20 to PATH_IRON_HAIR_001 and PATH_THYROID_HAIR_001",
        "no": "-0.10 from iron and thyroid pathways"
      }
    },
    {
      "q_id": "AQ003",
      "question": "Are your periods regular? (For female users)",
      "type": "boolean",
      "gender_filter": "female",
      "inference": {
        "no": "+0.30 to PATH_PCOS_HAIR_001. Load SCL_PCOS_001."
      }
    },
    {
      "q_id": "AQ004",
      "question": "Do you have acne or oily skin?",
      "type": "boolean",
      "inference": {
        "yes_with_irregular_periods": "+0.40 to PATH_PCOS_HAIR_001",
        "yes_alone": "+0.15 to DHT pathway"
      }
    },
    {
      "q_id": "AQ005",
      "question": "Do you drink tea or coffee with or right after meals?",
      "type": "frequency",
      "options": ["Never", "Sometimes", "Daily with meals"],
      "inference": {
        "Daily with meals": "Iron absorption blocker active — ref: ABS_IRON_001. +0.15 to PATH_IRON_HAIR_001"
      }
    },
    {
      "q_id": "AQ006",
      "question": "Do you feel cold easily or gain weight without changing diet?",
      "type": "boolean",
      "inference": {
        "yes": "+0.30 to PATH_THYROID_HAIR_001. Prompt LAB_TSH_001 recommendation."
      }
    },
    {
      "q_id": "AQ007",
      "question": "Do you eat meat, eggs, or fish regularly?",
      "type": "single_choice",
      "options": ["Yes, daily", "Yes, 2–3 times/week", "Rarely", "No, vegetarian", "No, vegan"],
      "inference": {
        "No, vegetarian": "+0.25 to PATH_IRON_HAIR_001 and B12 risk",
        "No, vegan": "+0.40 to B12 deficiency, +0.20 to iron"
      }
    },
    {
      "q_id": "AQ008",
      "question": "Have you had a major illness, surgery, or extremely stressful period in the last 3–6 months?",
      "type": "boolean",
      "inference": {
        "yes": "+0.35 to PATH_CORTISOL_HAIR_001 (telogen effluvium). Note: 2–3 month lag."
      }
    },
    {
      "q_id": "AQ009",
      "question": "Have you done any blood tests in the last 6 months?",
      "type": "boolean_with_data",
      "follow_up": "If yes — ask ferritin, Vitamin D, B12, TSH values",
      "inference": "Lab values override symptom-based probability scoring"
    },
    {
      "q_id": "AQ010",
      "question": "Did the hair fall increase after delivering a baby (in last 12 months)?",
      "type": "boolean",
      "gender_filter": "female",
      "inference": {
        "yes": "+0.80 to LIF_POSTPARTUM_001. Set as PROBABLE cause. Still check ferritin — often concurrent."
      }
    }
  ]
}
```

---

## 25_DECISION_ENGINE

```json
{
  "id": "DEC_HAIRFALL_FATIGUE_001",
  "node_type": "decision_rule",
  "version": "1.0",
  "name": "Hair Fall + Fatigue → Load Iron + Thyroid Pathways",
  "trigger_conditions": {
    "required": ["SYM_HAIRFALL_001", "SYM_FATIGUE_001"],
    "optional_boosters": ["SYM_DRYSKIN_001", "SYM_BRAINFOG_001", "AQ007_vegetarian"]
  },
  "action": "load_pathways",
  "pathways_loaded": ["PATH_IRON_HAIR_001", "PATH_THYROID_HAIR_001"],
  "routing_note": "Distinguish by cold intolerance (thyroid) vs pallor + dietary pattern (iron)"
}

{
  "id": "DEC_PCOS_CLUSTER_001",
  "node_type": "decision_rule",
  "version": "1.0",
  "name": "Hair Fall + Acne + Irregular Periods → PCOS Pathway",
  "trigger_conditions": {
    "required": ["SYM_HAIRFALL_001", "SYM_IRREGULARPERIODS_001"],
    "optional_boosters": ["SYM_ACNE_001", "SYM_WEIGHTGAIN_001"]
  },
  "action": "load_pathways",
  "pathways_loaded": ["PATH_PCOS_HAIR_001", "PATH_DHT_HAIR_001"],
  "routing_note": "Check insulin resistance markers. PCOS is insulin-driven in 70% of cases."
}

{
  "id": "DEC_POSTPARTUM_001",
  "node_type": "decision_rule",
  "version": "1.0",
  "name": "Post-Delivery Hair Fall → Postpartum + Iron",
  "trigger_conditions": {
    "required": ["SYM_HAIRFALL_001", "AQ010_postpartum_yes"]
  },
  "action": "load_pathways",
  "pathways_loaded": ["LIF_POSTPARTUM_001", "PATH_IRON_HAIR_001"],
  "routing_note": "Always check ferritin — delivery blood loss + breastfeeding deplete iron. Two causes often concurrent.",
  "important_message": "Explain postpartum effluvium is NORMAL and self-limiting. Manage anxiety."
}

{
  "id": "DEC_ACNE_HORMONAL_001",
  "node_type": "decision_rule",
  "version": "1.0",
  "name": "Acne + Oily Skin + Jawline Pattern → Hormonal Acne",
  "trigger_conditions": {
    "required": ["SYM_ACNE_001"],
    "location_pattern": "jawline_chin",
    "optional": ["SYM_IRREGULARPERIODS_001", "SYM_OILYSKIN_001"]
  },
  "action": "load_pathways",
  "pathways_loaded": ["PATH_PCOS_HAIR_001", "PATH_GUT_ACNE_001"],
  "routing_note": "Insulin-driven acne responds to low-GI diet. Gut acne needs microbiome repair."
}
```

---

## 26_ROOT_CAUSE_ENGINE

```json
{
  "id": "RCE_IRON_HAIR_001",
  "node_type": "root_cause",
  "version": "1.0",
  "name": "Iron Deficiency — Hair Loss Root Cause",
  "pathway_ref": "PATH_IRON_HAIR_001",
  "knowledge_refs_loaded": {
    "nutrition": "NUT_IRON_001",
    "absorption": "ABS_IRON_001",
    "biology": ["BIO_FOLLICLE_001", "BIO_MATRIX_001"],
    "lab": ["LAB_FERRITIN_001", "LAB_SERUM_IRON_001", "LAB_CRP_001"],
    "food": ["FOD_SPINACH_001", "FOD_RAJMA_001", "FOD_JAGGERY_001", "FOD_SESAME_001"]
  },
  "ai_assembly_instruction": "Load biological chain from PATH_IRON_HAIR_001. Load food sources from FOD nodes. Load absorption rules from ABS_IRON_001. Personalise based on diet pattern (vegetarian/non-veg) and tea/coffee habit.",
  "confidence_base": 0.72,
  "confidence_modifiers": {
    "vegetarian_diet": "+0.10",
    "heavy_periods": "+0.15",
    "ferritin_below_30_confirmed": "+0.30",
    "tea_with_meals": "+0.08",
    "fatigue_present": "+0.10"
  }
}

{
  "id": "RCE_DHT_HAIR_001",
  "node_type": "root_cause",
  "version": "1.0",
  "name": "DHT Excess — Hair Loss Root Cause",
  "pathway_ref": "PATH_DHT_HAIR_001",
  "knowledge_refs_loaded": {
    "hormone": "HOR_DHT_001",
    "biology": ["BIO_DERMALPAPILLA_001", "BIO_FOLLICLE_001"],
    "medical": "MED_PCOS_001",
    "genetics": "GEN_ANDROGEN_SENSITIVITY_001",
    "blood_sugar": "BLD_INSULIN_RESISTANCE_001",
    "lab": ["LAB_FREE_TESTOSTERONE_001", "LAB_SHBG_001", "LAB_FASTING_INSULIN_001"]
  },
  "confidence_base": 0.65,
  "confidence_modifiers": {
    "patterned_recession": "+0.20",
    "family_history_baldness": "+0.15",
    "acne_present": "+0.10",
    "irregular_periods": "+0.15",
    "testosterone_elevated_confirmed": "+0.35"
  }
}

{
  "id": "RCE_PCOS_001",
  "node_type": "root_cause",
  "version": "1.0",
  "name": "PCOS — Multi-Symptom Root Cause",
  "pathway_ref": "PATH_PCOS_HAIR_001",
  "knowledge_refs_loaded": {
    "medical": "MED_PCOS_001",
    "hormones": ["HOR_INSULIN_001", "HOR_DHT_001", "HOR_LH_001"],
    "blood_sugar": "BLD_INSULIN_RESISTANCE_001",
    "inflammation": "INF_CHRONIC_001",
    "lab": ["LAB_FREE_TESTOSTERONE_001", "LAB_DHEAS_001", "LAB_LH_FSH_RATIO_001", "LAB_FASTING_INSULIN_001"]
  },
  "confidence_base": 0.75,
  "confidence_modifiers": {
    "irregular_periods": "+0.25",
    "acne_plus_hair_fall": "+0.20",
    "weight_gain_plus_irregular_periods": "+0.20",
    "lh_fsh_ratio_above_2_confirmed": "+0.40"
  }
}
```

---

## 27_SYMPTOM_CLUSTERS

```json
{
  "id": "SCL_IRON_001",
  "node_type": "symptom_cluster",
  "version": "1.0",
  "name": "Iron Deficiency Cluster",
  "required_symptoms": ["SYM_HAIRFALL_001", "SYM_FATIGUE_001"],
  "supporting_symptoms": ["SYM_BRAINFOG_001", "SYM_DRYSKIN_001"],
  "lifestyle_signals": ["vegetarian", "heavy_periods", "tea_with_meals"],
  "confidence_required_only": 0.55,
  "confidence_with_all_supporting": 0.88,
  "root_cause_ref": "RCE_IRON_HAIR_001",
  "pathway_ref": "PATH_IRON_HAIR_001",
  "lab_confirmations": ["LAB_FERRITIN_001", "LAB_SERUM_IRON_001", "LAB_CRP_001"]
}

{
  "id": "SCL_PCOS_001",
  "node_type": "symptom_cluster",
  "version": "1.0",
  "name": "PCOS Cluster",
  "required_symptoms": ["SYM_IRREGULARPERIODS_001"],
  "supporting_symptoms": ["SYM_HAIRFALL_001", "SYM_ACNE_001", "SYM_WEIGHTGAIN_001"],
  "gender_filter": "female",
  "confidence_required_only": 0.45,
  "confidence_with_2_supporting": 0.75,
  "confidence_with_all_supporting": 0.92,
  "root_cause_ref": "RCE_PCOS_001",
  "pathway_ref": "PATH_PCOS_HAIR_001",
  "lab_confirmations": ["LAB_FREE_TESTOSTERONE_001", "LAB_FASTING_INSULIN_001", "LAB_LH_FSH_RATIO_001"]
}

{
  "id": "SCL_THYROID_001",
  "node_type": "symptom_cluster",
  "version": "1.0",
  "name": "Hypothyroid Cluster",
  "required_symptoms": ["SYM_FATIGUE_001"],
  "supporting_symptoms": ["SYM_HAIRFALL_001", "SYM_WEIGHTGAIN_001", "SYM_DRYSKIN_001", "SYM_BRAINFOG_001"],
  "clinical_hallmarks": ["Cold intolerance", "Constipation", "Outer eyebrow thinning", "Puffy face"],
  "confidence_required_only": 0.30,
  "confidence_with_3_supporting": 0.72,
  "root_cause_ref": "RCE_THYROID_HAIR_001",
  "pathway_ref": "PATH_THYROID_HAIR_001",
  "lab_confirmations": ["LAB_TSH_001", "LAB_FT3_001", "LAB_FT4_001", "LAB_ANTI_TPO_001"]
}
```

---

## 28_CONFIDENCE_ENGINE

```json
{
  "id": "CON_SCHEMA_001",
  "node_type": "confidence_engine_schema",
  "version": "1.0",
  "description": "Schema for how confidence results are structured for any user session.",
  "output_schema": {
    "user_session": "string — session ID",
    "input_symptoms": ["array of SYM_ IDs"],
    "input_lifestyle": "object — diet, stress, sleep, exercise",
    "input_labs": "object — any confirmed lab values",
    "ranked_causes": [
      {
        "rank": "integer",
        "root_cause_ref": "RCE_ ID",
        "pathway_ref": "PATH_ ID",
        "confidence_score": "0.00–1.00",
        "confidence_label": "High / Moderate / Low",
        "key_evidence": ["array of supporting factors"],
        "missing_data": ["what would raise or lower confidence"],
        "lab_recommendation": ["LAB_ IDs to confirm"]
      }
    ],
    "recommended_action": "INT_ ID",
    "recommended_labs": ["LAB_ IDs prioritised by diagnostic value"],
    "uncertainty_flag": "boolean — if top two causes within 0.10 of each other, flag for lab confirmation before intervention"
  },
  "uncertainty_rule": "If confidence_score difference between rank 1 and rank 2 is less than 0.15, DO NOT commit to intervention. Recommend labs first.",
  "hallucination_guard": "Every claim in output MUST have a node_ref. No free-text medical claims without reference."
}

{
  "id": "CON_EXAMPLE_001",
  "node_type": "confidence_result_example",
  "version": "1.0",
  "user_session": "session_demo_001",
  "input_symptoms": ["SYM_HAIRFALL_001", "SYM_FATIGUE_001"],
  "input_lifestyle": {
    "diet": "vegetarian",
    "tea_with_meals": true,
    "periods": "regular",
    "stress": "moderate",
    "sleep": "6 hours"
  },
  "input_labs": null,
  "ranked_causes": [
    {
      "rank": 1,
      "root_cause_ref": "RCE_IRON_HAIR_001",
      "pathway_ref": "PATH_IRON_HAIR_001",
      "confidence_score": 0.84,
      "confidence_label": "High",
      "key_evidence": [
        "Vegetarian diet — limited heme iron",
        "Tea with meals — blocks iron absorption (ref: ABS_IRON_001)",
        "Hair fall + fatigue — classic iron cluster (ref: SCL_IRON_001)",
        "Female reproductive age — higher iron demand"
      ],
      "missing_data": ["Ferritin value would confirm or refute at high certainty"],
      "lab_recommendation": ["LAB_FERRITIN_001", "LAB_CRP_001"]
    },
    {
      "rank": 2,
      "root_cause_ref": "RCE_THYROID_HAIR_001",
      "pathway_ref": "PATH_THYROID_HAIR_001",
      "confidence_score": 0.48,
      "confidence_label": "Moderate",
      "key_evidence": ["Fatigue present", "Hair fall present"],
      "missing_data": ["No cold intolerance, weight gain, or constipation reported — reduces probability"],
      "lab_recommendation": ["LAB_TSH_001", "LAB_FT3_001"]
    },
    {
      "rank": 3,
      "root_cause_ref": "RCE_DHT_HAIR_001",
      "pathway_ref": "PATH_DHT_HAIR_001",
      "confidence_score": 0.28,
      "confidence_label": "Low",
      "key_evidence": ["No acne, regular periods, no pattern recession reported"],
      "lab_recommendation": null
    }
  ],
  "recommended_action": "INT_IRON_001",
  "recommended_labs": ["LAB_FERRITIN_001", "LAB_CRP_001", "LAB_TSH_001"],
  "uncertainty_flag": false
}
```

---

---

# LAYER 3 — ACTION

---

## 29_INTERVENTION_ENGINE

```json
{
  "id": "INT_IRON_001",
  "node_type": "intervention",
  "version": "1.0",
  "name": "Iron Deficiency Intervention Plan",
  "root_cause_ref": "RCE_IRON_HAIR_001",
  "pathway_ref": "PATH_IRON_HAIR_001",
  "minimum_confidence_to_fire": 0.55,
  "sections": {
    "nutrition": {
      "increase": [
        { "food_ref": "FOD_SPINACH_001", "frequency": "Daily", "tip": "Cook palak with 1 tsp lemon juice squeezed after cooking. Pair with dal at lunch." },
        { "food_ref": "FOD_RAJMA_001", "frequency": "3x/week", "tip": "Soak overnight. Eat with chaas or salad containing lemon." },
        { "food_ref": "FOD_SESAME_001", "frequency": "Daily 1 tbsp", "tip": "Til chutney or roasted til laddoo as snack." },
        { "food_ref": "FOD_JAGGERY_001", "frequency": "Daily small piece", "tip": "Replace refined sugar in chai with jaggery post-meal gap." },
        { "food_ref": "FOD_AMLA_001", "frequency": "Daily", "tip": "Amla with every iron-rich meal as Vitamin C enhancer." }
      ],
      "reduce": [
        { "item": "Tea/coffee at mealtimes", "reason_ref": "ABS_IRON_001", "instruction": "Wait minimum 45–60 minutes before or after iron-rich meal." },
        { "item": "Calcium-rich dairy at same meal as iron", "reason_ref": "ABS_IRON_001" }
      ],
      "supplement": {
        "condition": "Ferritin < 30 ng/mL or Hb < 12 g/dL",
        "recommendation": "Iron bisglycinate 25–36 mg daily (gentler form, less constipation than ferrous sulphate)",
        "timing": "Morning, empty stomach with 100mg Vitamin C (amla juice/lemon water)",
        "duration": "3–6 months minimum",
        "monitoring_ref": "LAB_FERRITIN_001",
        "medical_supervision_trigger": "Hb < 10 g/dL — refer to physician"
      }
    },
    "lifestyle": {
      "sleep": {
        "instruction": "7–8 hours. Deep sleep supports GH-IGF-1 axis — critical for follicle recovery.",
        "ref": "SLP_DEEPSLEEP_001"
      },
      "stress": {
        "instruction": "Chronic stress elevates cortisol → impairs iron absorption and prolongs telogen.",
        "ref": "STR_CHRONIC_001",
        "action": "Daily 10-minute deep breathing or yoga nidra"
      },
      "exercise": {
        "instruction": "30 min aerobic exercise 4x/week improves scalp circulation and mitochondrial efficiency.",
        "ref": "EXE_AEROBIC_001"
      }
    },
    "medical_referral": {
      "trigger_conditions": [
        "Ferritin < 12 ng/mL",
        "Hb < 10 g/dL",
        "No improvement in ferritin after 3 months of intervention",
        "Suspected H. pylori or celiac (persistent low ferritin despite good diet)"
      ],
      "specialist": "General physician or gastroenterologist"
    }
  },
  "progress_ref": "PRG_IRON_001",
  "expected_timeline": "Energy improvement: 4–6 weeks. Hair shedding reduction: 6–8 weeks. Hair density visible improvement: 4–6 months."
}

{
  "id": "INT_PCOS_001",
  "node_type": "intervention",
  "version": "1.0",
  "name": "PCOS Intervention Plan",
  "root_cause_ref": "RCE_PCOS_001",
  "pathway_ref": "PATH_PCOS_HAIR_001",
  "minimum_confidence_to_fire": 0.60,
  "sections": {
    "nutrition": {
      "strategy": "Low glycaemic index diet to reduce insulin resistance — the primary driver",
      "increase": [
        { "food_ref": "FOD_DAL_001", "tip": "Replace refined carbs with dal-based meals" },
        { "food_ref": "FOD_PUMPKIN_SEEDS_001", "tip": "Daily 30g for zinc-mediated DHT inhibition (ref: NUT_ZINC_001)" },
        { "item": "Cinnamon 1 tsp/day", "mechanism": "Improves insulin sensitivity" }
      ],
      "reduce": [
        { "item": "White rice, maida, sugar, sugary drinks", "reason": "Spikes insulin → drives androgen production (ref: HOR_INSULIN_001)" }
      ],
      "supplement": {
        "inositol": "Myo-inositol 2g + D-chiro-inositol 50mg daily (evidence-based for PCOS insulin sensitivity)",
        "zinc": "Zinc 25mg daily (DHT inhibition — ref: NUT_ZINC_001)",
        "condition": "Always under medical guidance for PCOS supplements"
      }
    },
    "lifestyle": {
      "exercise": {
        "instruction": "Resistance training 3x/week + walking 30 min daily. Proven to reduce insulin resistance significantly.",
        "ref": "EXE_RESISTANCE_001"
      },
      "sleep": {
        "instruction": "7–9 hours. Sleep deprivation worsens insulin resistance directly.",
        "ref": "SLP_DEEPSLEEP_001"
      },
      "stress": {
        "instruction": "Cortisol worsens PCOS inflammation. Daily stress management critical.",
        "ref": "STR_CHRONIC_001"
      }
    },
    "medical_referral": {
      "trigger_conditions": ["Confirmed PCOS on ultrasound or lab", "Trying to conceive", "Severe symptoms unresponsive to lifestyle"],
      "specialist": "Gynecologist / Endocrinologist"
    }
  },
  "progress_ref": "PRG_PCOS_001"
}

{
  "id": "INT_STRESS_001",
  "node_type": "intervention",
  "version": "1.0",
  "name": "Chronic Stress / Cortisol Intervention Plan",
  "root_cause_ref": "RCE_CORTISOL_HAIR_001",
  "pathway_ref": "PATH_CORTISOL_HAIR_001",
  "sections": {
    "nutrition": {
      "increase": [
        { "food_ref": "FOD_PUMPKIN_SEEDS_001", "reason": "Magnesium — cortisol buffering (ref: NUT_MAGNESIUM_001)" },
        { "food_ref": "FOD_BANANA_001", "reason": "Magnesium + potassium + Vitamin B6 — stress support" },
        { "food_ref": "FOD_AMLA_001", "reason": "Vitamin C — adrenal cortisol regulation (ref: NUT_VITC_001)" }
      ],
      "reduce": [
        { "item": "Caffeine after 2 PM", "reason": "Extends cortisol elevation, disrupts evening wind-down" }
      ],
      "supplement": {
        "magnesium_glycinate": "200–400 mg before bed (sleep + cortisol modulation)",
        "ashwagandha": "300–600 mg KSM-66 extract (adaptogen — cortisol reduction — evidence-based)"
      }
    },
    "lifestyle": {
      "sleep_priority": "Non-negotiable. Sleep debt is both a cause and consequence of high cortisol. (ref: SLP_CIRCADIAN_001)",
      "stress_practices": ["Yoga nidra", "Box breathing", "Progressive muscle relaxation", "Daily 10-min walk in nature"],
      "exercise": "Moderate aerobic > intense (high-intensity training elevates cortisol further in already-stressed individuals)"
    },
    "important_note": "Hair will not recover until cortisol is regulated. Hair intervention alone will not work."
  },
  "progress_ref": "PRG_STRESS_001"
}

{
  "id": "INT_GUT_001",
  "node_type": "intervention",
  "version": "1.0",
  "name": "Gut Health Restoration Plan",
  "root_cause_ref": "RCE_DYSBIOSIS_GUT_001",
  "pathway_ref": "PATH_GUT_ACNE_001",
  "sections": {
    "nutrition": {
      "increase": [
        { "item": "Fermented foods", "examples": ["Curd", "Kanji", "Idli/Dosa (fermented)"], "reason": "Probiotic species — Lactobacillus, Bifidobacterium" },
        { "item": "Prebiotic foods", "examples": ["Onion", "Garlic", "Banana", "Oats"], "reason": "Feed beneficial bacteria" },
        { "item": "Diverse plant foods", "target": "30 different plant foods per week", "reason": "Increases microbiome diversity" }
      ],
      "reduce": [
        { "item": "Ultra-processed foods, sugar", "reason": "Feeds pathogenic bacteria, disrupts microbiome" },
        { "item": "Antibiotics unless necessary", "reason": "ref: MEDS_ANTIBIOTICS_001 — wipe microbiome" }
      ],
      "supplement": {
        "probiotic": "Multi-strain probiotic (Lactobacillus acidophilus + Bifidobacterium longum) — 10 billion CFU daily with meals",
        "zinc": "Zinc 25mg (tight junction repair — ref: NUT_ZINC_001, BIO_GUTLINING_001)"
      }
    },
    "lifestyle": {
      "stress": "Stress directly disrupts gut motility and microbiome. Stress management is gut health. (ref: STR_CHRONIC_001)",
      "sleep": "Gut microbiome follows circadian rhythm. Irregular sleep disrupts microbiome. (ref: SLP_CIRCADIAN_001)"
    }
  },
  "progress_ref": "PRG_GUT_001"
}
```

---

## 30_PROGRESS_ENGINE

```json
{
  "id": "PRG_IRON_001",
  "node_type": "progress_tracker",
  "version": "1.0",
  "intervention_ref": "INT_IRON_001",
  "root_cause_ref": "RCE_IRON_HAIR_001",
  "milestones": [
    {
      "week": 2,
      "check": "Are you avoiding tea/coffee with meals consistently?",
      "habit_target": "iron_absorption_protocol",
      "expected": "No measurable hair change yet — building iron stores."
    },
    {
      "week": 4,
      "check": "Has your energy level improved, even slightly?",
      "lab": null,
      "expected": "Energy often improves before hair — iron is prioritised to RBCs over follicles."
    },
    {
      "week": 8,
      "check": "Has daily hair fall count reduced?",
      "lab": "LAB_FERRITIN_001",
      "expected": "Ferritin should rise 10–20 ng/mL. Shedding should reduce.",
      "if_no_improvement": "Re-trigger Decision Engine. Check absorption (H. pylori?). Review supplement compliance."
    },
    {
      "week": 16,
      "check": "Can you see new baby hairs at your hairline?",
      "lab": "LAB_FERRITIN_001",
      "expected": "Ferritin > 50 ng/mL. New terminal hairs visible.",
      "if_no_improvement": "Rule out concurrent thyroid or androgen cause. Refer physician."
    },
    {
      "week": 24,
      "check": "Is hair density visibly improved compared to 6 months ago?",
      "lab": "LAB_FERRITIN_001",
      "expected": "Ferritin 70+ ng/mL. Significant density return. Maintenance phase begins."
    }
  ],
  "habit_tracking": [
    "iron_rich_meals_per_day",
    "tea_coffee_gap_maintained",
    "vitamin_c_with_meals",
    "sleep_hours_per_night",
    "supplement_taken_daily"
  ],
  "feedback_loop": {
    "on_track": "Positive reinforcement. Celebrate small milestones.",
    "off_track_8_weeks": "Re-load AI Questions. Consider concurrent cause. Check absorption.",
    "regression": "Re-run Confidence Engine with updated inputs."
  }
}

{
  "id": "PRG_PCOS_001",
  "node_type": "progress_tracker",
  "version": "1.0",
  "intervention_ref": "INT_PCOS_001",
  "root_cause_ref": "RCE_PCOS_001",
  "milestones": [
    {
      "week": 4,
      "check": "Have you reduced refined carbs and sugar?",
      "expected": "Energy stabilisation. Reduced post-meal crashes."
    },
    {
      "week": 8,
      "check": "Any improvement in period regularity?",
      "lab": "LAB_FASTING_INSULIN_001",
      "expected": "Fasting insulin should reduce. Cycle may slightly regularise."
    },
    {
      "week": 12,
      "check": "Has acne reduced? Hair fall slowing?",
      "lab": "LAB_FREE_TESTOSTERONE_001",
      "expected": "Testosterone levels beginning to normalise with insulin reduction."
    },
    {
      "week": 24,
      "check": "Periods regular? Hair density improving?",
      "lab": ["LAB_FASTING_INSULIN_001", "LAB_FREE_TESTOSTERONE_001"],
      "expected": "Significant hormonal improvement with sustained lifestyle change."
    }
  ],
  "important_note": "PCOS is a chronic condition requiring long-term lifestyle management. Set realistic expectations."
}
```

---

---

# ANTI-DUPLICATION ENFORCEMENT RULES

## The Single-Source Table

| Information | Only Stored In | Referenced From |
|-------------|----------------|-----------------|
| Iron biology | `NUT_IRON_001` | BIO, SYM, PATH, RCE, INT, PRG nodes |
| Hair follicle biology | `BIO_FOLLICLE_001` | SYS, SYM, PATH, RCE nodes |
| Iron absorption rules | `ABS_IRON_001` | INT, RCE, AIQ nodes |
| Ferritin ranges | `LAB_FERRITIN_001` | INT, PRG, RCE, CON nodes |
| PCOS diagnosis | `MED_PCOS_001` | SCL, RCE, DEC, INT nodes |
| Thyroid hormone function | `HOR_THYROID_001` | SYS, PATH, RCE, INT nodes |
| Food nutrient values | `FOD_*` nodes | INT, NUT nodes only |
| Lab ranges | `LAB_*` nodes | RCE, CON, INT, PRG nodes |
| Biological chains | `PATH_*` nodes | RCE, DEC, CON nodes |

**Enforcement:** If a developer finds nutrient biology described in a Symptom node, a Pathway node, or an Intervention node — it is a duplication violation. Delete from there, add a `ref` pointer to the `NUT_` node instead.

---

# RAG ACCURACY DESIGN

## Why This Architecture Prevents Hallucination

| Mechanism | How It Works |
|-----------|-------------|
| **Ref-only assembly** | The AI loads facts via `node_ref` — it cannot invent biology because all biology is stored in discrete nodes |
| **Pathway tracing** | Every answer must follow PATH_ chain. No answer without a biological chain. |
| **Confidence gating** | Intervention only fires above `minimum_confidence_to_fire`. Low-confidence → ask more questions or recommend labs. |
| **Uncertainty flag** | If top 2 causes are within 0.15 confidence, flag → recommend labs before action |
| **India-specific grounding** | Prevalence data, food database, lab costs anchored to Indian context → no generic Western answers |
| **Lab validation loop** | PRG_ nodes re-trigger RCE_ at each milestone if no improvement → self-correcting system |
| **node_type field** | AI always knows if it is reading a fact (biology), a rule (decision), or an action (intervention) |

## Token Efficiency Design

| Design Choice | Token Savings |
|---------------|--------------|
| Biology stored once in BIO_ → referenced everywhere | ~60% reduction vs duplicating in every answer |
| Pathways pre-assemble biological chain | AI loads PATH_ directly instead of reasoning from scratch |
| Symptom → Cluster → Pathway routing | Avoids loading all 30 layers for every query — only relevant nodes loaded |
| Confidence scoring narrows loaded nodes | High-confidence result loads fewer competing pathway nodes |

---

# MASTER QUERY FLOW (Complete)

```
User: "I have hair fall, I feel very tired, I am vegetarian, I drink chai with meals"
         ↓
[03_SYMPTOMS] Load: SYM_HAIRFALL_001 + SYM_FATIGUE_001
         ↓
[27_SYMPTOM_CLUSTERS] Match: SCL_IRON_001 → confidence 0.55
         ↓
[24_AI_QUESTIONS] Fire AIQ_HAIRFALL_001:
   AQ002: Fatigue → confirmed → +0.10
   AQ005: Chai with meals → confirmed → +0.15 to iron pathway
   AQ007: Vegetarian → confirmed → +0.25
   AQ003: Periods regular → -0.20 from PCOS
         ↓
Running confidence: Iron 0.84 | Thyroid 0.48 | PCOS 0.28
         ↓
[25_DECISION_ENGINE] DEC_HAIRFALL_FATIGUE_001 → Load PATH_IRON_HAIR_001 + PATH_THYROID_HAIR_001
         ↓
[26_ROOT_CAUSE_ENGINE] RCE_IRON_HAIR_001 activates:
   → NUT_IRON_001 (iron biology)
   → BIO_FOLLICLE_001 + BIO_MATRIX_001 (hair biology)
   → ABS_IRON_001 (absorption rules — chai blocking confirmed)
   → LAB_FERRITIN_001 (range thresholds)
   → FOD_SPINACH_001, FOD_RAJMA_001, FOD_SESAME_001, FOD_AMLA_001 (India-specific foods)
         ↓
[28_CONFIDENCE_ENGINE] Output CON_EXAMPLE_001:
   #1 Iron 0.84 (High) — Recommend INT_IRON_001
   #2 Thyroid 0.48 (Moderate) — Recommend LAB_TSH_001 to confirm/rule out
   Uncertainty flag: false (gap >0.15)
         ↓
[29_INTERVENTION_ENGINE] INT_IRON_001 personalised:
   → Iron-rich Indian foods for vegetarian
   → Chai separation protocol (from ABS_IRON_001)
   → Amla Vitamin C pairing (from FOD_AMLA_001, NUT_VITC_001)
   → Supplement if ferritin <30
         ↓
[30_PROGRESS_ENGINE] PRG_IRON_001:
   Week 2 → Habit check
   Week 4 → Energy check
   Week 8 → Ferritin lab + hair fall check
   Week 16 → Density check
   If off-track → re-trigger AIQ + RCE
```

---

> [!IMPORTANT]
> **This architecture is finalized and ready for implementation.**
> Start by building the full Iron, PCOS, and Thyroid pathways completely in a JSON file, validate the reference chain, then expand node by node. Never expand a layer before the chain from SYS_ → BIO_ → SYM_ → PATH_ → RCE_ → INT_ → PRG_ is verified for one complete pathway.
