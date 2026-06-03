# HealthSync RAG — Part 2: Remaining Pathways · Missing Interventions · Progress Trackers · Full Node Registry

---

## WHAT THIS DOCUMENT COMPLETES

Part 1 established the full architecture skeleton and the Iron, DHT, Thyroid, PCOS, Cortisol, and Gut pathways in detail.

**Part 2 completes:**
1. Remaining Pathways — Vitamin D, Protein, B12, Postpartum, Omega-3, Insulin-Acne
2. Missing Intervention nodes — Thyroid, DHT
3. All remaining Progress Tracker nodes
4. Complete Node Registry — every node ID across all 30 layers
5. Cross-Reference Validation Rules
6. Developer Implementation Guide

---

---

# REMAINING PATHWAYS (23_PATHWAYS continued)

---

```json
{
  "id": "PATH_VITD_HAIR_001",
  "node_type": "pathway",
  "version": "1.0",
  "name": "Vitamin D Deficiency → Hair Loss Pathway",
  "root_cause": "Low Vitamin D — VDR underactivation in hair follicle",
  "terminal_symptom": "SYM_HAIRFALL_001",
  "confidence_base": 0.58,
  "prevalence_india": "70–90% of Indians are Vitamin D insufficient or deficient despite high sun exposure — indoor lifestyle, dark skin, clothing",
  "biological_chain": [
    {
      "step": 1,
      "node_ref": "NUT_VITD_001",
      "event": "25(OH)D levels fall below 30 ng/mL",
      "mechanism": "Inadequate sun exposure or dietary intake. Fat malabsorption can impair uptake."
    },
    {
      "step": 2,
      "node_ref": "BIO_FOLLICLE_001",
      "event": "Vitamin D Receptor (VDR) in hair follicle bulge underactivated",
      "mechanism": "VDR in bulge stem cells is required to initiate anagen. Without activation, follicle stays in telogen."
    },
    {
      "step": 3,
      "node_ref": "BIO_FOLLICLE_001",
      "event": "Anagen initiation fails — follicle remains in prolonged telogen",
      "mechanism": "VDR knockout mouse models show arrested hair cycling — strong mechanistic evidence"
    },
    {
      "step": 4,
      "node_ref": "SYM_HAIRFALL_001",
      "event": "Chronic diffuse shedding, slow regrowth after shedding episodes",
      "mechanism": "Hairs shed normally but new anagen cannot initiate efficiently"
    }
  ],
  "amplifying_factors": [
    { "factor": "ABS_VITD_001", "description": "Fat malabsorption (Celiac, IBS) reduces absorption of this fat-soluble vitamin" },
    { "factor": "INF_CHRONIC_001", "description": "Inflammation increases Vitamin D catabolism — deficiency worsens faster" },
    { "factor": "MED_HYPOTHYROID_001", "description": "Hashimoto's thyroiditis (autoimmune) risk increases with low Vitamin D" },
    { "factor": "OXI_FREE_RADICAL_001", "description": "Vitamin D is antioxidant — deficiency increases oxidative follicle damage" }
  ],
  "distinguishing_from": {
    "PATH_IRON_HAIR_001": "Both cause diffuse loss. Iron → more fatigue, pallor. Vitamin D → more mood/immune issues.",
    "PATH_THYROID_HAIR_001": "Vitamin D deficiency can CAUSE autoimmune thyroiditis — these are often concurrent"
  },
  "lab_confirmation": ["LAB_VITD_001"],
  "intervention_ref": "INT_VITD_001"
}

{
  "id": "PATH_PROTEIN_HAIR_001",
  "node_type": "pathway",
  "version": "1.0",
  "name": "Protein Deficiency → Hair Loss Pathway",
  "root_cause": "Inadequate dietary protein → insufficient keratin synthesis",
  "terminal_symptom": "SYM_HAIRFALL_001",
  "confidence_base": 0.55,
  "prevalence_india": "Common in crash dieters, young women on calorie restriction, elderly, and some strict vegetarians with poorly planned diets",
  "biological_chain": [
    {
      "step": 1,
      "node_ref": "NUT_PROTEIN_001",
      "event": "Dietary protein intake falls below 0.8g/kg body weight",
      "mechanism": "Body enters net negative protein balance — insufficient amino acids for all protein-dependent functions"
    },
    {
      "step": 2,
      "node_ref": "BIO_HAIRBULB_001",
      "event": "Body prioritises vital organs for amino acids — hair follicle protein synthesis deprioritised",
      "mechanism": "Triage response: liver, immune, cardiac proteins maintained. Hair is physiologically non-essential."
    },
    {
      "step": 3,
      "node_ref": "BIO_MATRIX_001",
      "event": "Keratin synthesis insufficient — hair shaft becomes weak, thin",
      "mechanism": "Keratin is 95% protein. Cysteine, methionine amino acid availability critical."
    },
    {
      "step": 4,
      "node_ref": "BIO_FOLLICLE_001",
      "event": "Follicle enters telogen effluvium — mass shedding",
      "mechanism": "Severe protein restriction can trigger synchronised telogen entry within 2–3 months"
    },
    {
      "step": 5,
      "node_ref": "SYM_HAIRFALL_001",
      "event": "Diffuse shedding, brittle hair, slow regrowth",
      "mechanism": "Both structural weakness (thin shaft) and shedding (telogen) occur simultaneously"
    }
  ],
  "amplifying_factors": [
    { "factor": "GUT_MALABSORPTION_001", "description": "Poor gut health impairs amino acid absorption from dietary protein" },
    { "factor": "STR_CHRONIC_001", "description": "Stress increases protein catabolism — worsens deficit" }
  ],
  "common_pattern_india": "Young women doing 'diet' with only fruits, salads, very little dal/eggs/paneer. Protein intake often as low as 20–30g/day vs 50–60g requirement.",
  "lab_confirmation": ["LAB_SERUM_ALBUMIN_001", "LAB_TOTAL_PROTEIN_001"],
  "intervention_ref": "INT_PROTEIN_001"
}

{
  "id": "PATH_B12_HAIR_001",
  "node_type": "pathway",
  "version": "1.0",
  "name": "Vitamin B12 Deficiency → Hair Loss Pathway",
  "root_cause": "B12 deficiency → impaired RBC maturation → reduced oxygen to follicle",
  "terminal_symptom": "SYM_HAIRFALL_001",
  "confidence_base": 0.52,
  "prevalence_india": "Extremely common — 47–80% of vegetarians in India have B12 insufficiency",
  "biological_chain": [
    {
      "step": 1,
      "node_ref": "NUT_B12_001",
      "event": "B12 levels fall below 300 pg/mL (functional deficiency threshold)",
      "mechanism": "Vegetarian diet provides no B12. Gut absorption impaired by PPIs or Metformin."
    },
    {
      "step": 2,
      "node_ref": "BIO_MITOCHONDRIA_001",
      "event": "DNA synthesis impaired — megaloblastic changes in RBC precursors",
      "mechanism": "B12 is cofactor for methionine synthase — required for DNA methylation and synthesis in all rapidly dividing cells"
    },
    {
      "step": 3,
      "node_ref": "BIO_MATRIX_001",
      "event": "Matrix cells (rapid dividers) also affected by impaired DNA synthesis",
      "mechanism": "Hair matrix cells divide every 12–24 hours — same impairment as RBC precursors"
    },
    {
      "step": 4,
      "node_ref": "SYM_HAIRFALL_001",
      "event": "Diffuse hair shedding — often combined with premature greying",
      "mechanism": "B12 deficiency causes both telogen effluvium and reduced melanocyte function → greying"
    }
  ],
  "distinguishing_signs": [
    "Premature greying (early grey hair) — B12 specific sign",
    "Tingling/numbness in hands or feet — neurological B12 deficiency sign",
    "Elevated MCV on CBC — megaloblastic anaemia"
  ],
  "amplifying_factors": [
    { "factor": "ABS_B12_001", "description": "Vegetarian diet + PPI use = double risk" },
    { "factor": "MEDS_METFORMIN_001", "description": "Metformin users must monitor B12 annually" }
  ],
  "lab_confirmation": ["LAB_B12_001", "LAB_MCV_001", "LAB_HOMOCYSTEINE_001"],
  "intervention_ref": "INT_B12_001"
}

{
  "id": "PATH_POSTPARTUM_HAIR_001",
  "node_type": "pathway",
  "version": "1.0",
  "name": "Postpartum Telogen Effluvium Pathway",
  "root_cause": "Postpartum estrogen drop → synchronised telogen entry → mass shedding",
  "terminal_symptom": "SYM_HAIRFALL_001",
  "confidence_base": 0.92,
  "important_flag": "PHYSIOLOGICAL — NOT PATHOLOGICAL. Requires reassurance first, investigation for concurrent causes second.",
  "biological_chain": [
    {
      "step": 1,
      "node_ref": "LIF_POSTPARTUM_001",
      "event": "Estrogen and progesterone drop sharply after delivery",
      "mechanism": "During pregnancy, high estrogen prolonged anagen — up to 95% of follicles in anagen"
    },
    {
      "step": 2,
      "node_ref": "HOR_ESTROGEN_001",
      "event": "Sudden estrogen withdrawal signals mass follicle telogen entry",
      "mechanism": "Loss of anagen-prolonging estrogen signal → all held-in-anagen follicles synchronise into telogen"
    },
    {
      "step": 3,
      "node_ref": "BIO_FOLLICLE_001",
      "event": "Telogen phase completes (3–4 months) → mass shedding begins",
      "mechanism": "2–4 months after delivery, all synchronised follicles shed simultaneously"
    },
    {
      "step": 4,
      "node_ref": "SYM_HAIRFALL_001",
      "event": "Dramatic hair shedding — often alarming to mother. Peak at 3–6 months postpartum.",
      "mechanism": "Physiological mass telogen effluvium. Self-limiting by 9–12 months."
    }
  ],
  "concurrent_risk": {
    "iron_deficiency": "Delivery blood loss + breastfeeding increases iron demand dramatically. Check ferritin alongside.",
    "thyroid": "Postpartum thyroiditis occurs in 5–10% of women. Check TSH if shedding extends beyond 9 months.",
    "ref": "PATH_IRON_HAIR_001 often concurrent"
  },
  "reassurance_message": "This is one of the most common and normal postpartum experiences. Hair fully recovers by 9–12 months if nutritional support is adequate.",
  "lab_confirmation": ["LAB_FERRITIN_001", "LAB_TSH_001", "LAB_VITD_001"],
  "intervention_ref": "INT_POSTPARTUM_001"
}

{
  "id": "PATH_INSULIN_ACNE_001",
  "node_type": "pathway",
  "version": "1.0",
  "name": "Insulin Resistance → IGF-1 → Acne Pathway",
  "root_cause": "Hyperinsulinemia and IGF-1 elevation → sebum overproduction → acne",
  "terminal_symptom": "SYM_ACNE_001",
  "confidence_base": 0.68,
  "biological_chain": [
    {
      "step": 1,
      "node_ref": "BLD_INSULIN_RESISTANCE_001",
      "event": "High glycaemic diet → glucose spike → insulin surge",
      "mechanism": "Refined carbohydrates, sugar, maida → rapid glucose absorption → hyperinsulinemia"
    },
    {
      "step": 2,
      "node_ref": "HOR_INSULIN_001",
      "event": "Insulin stimulates liver IGF-1 production and reduces IGFBP-3",
      "mechanism": "High insulin → elevated free IGF-1 bioavailability"
    },
    {
      "step": 3,
      "node_ref": "BIO_SEBGLAND_001",
      "event": "IGF-1 stimulates sebocyte proliferation and sebum output",
      "mechanism": "IGF-1 receptor on sebaceous glands → increased lipogenesis in sebocytes"
    },
    {
      "step": 4,
      "node_ref": "BIO_EPIDERMIS_001",
      "event": "Insulin also increases keratinocyte stickiness — pore lining sheds abnormally",
      "mechanism": "IGF-1 promotes keratinocyte proliferation → comedone formation"
    },
    {
      "step": 5,
      "node_ref": "SYM_ACNE_001",
      "event": "Comedonal and inflammatory acne — particularly forehead, cheeks, upper back",
      "mechanism": "Excess sebum + blocked pore + P. acnes proliferation = inflammatory lesion"
    }
  ],
  "amplifying_factors": [
    { "factor": "HOR_DHT_001", "description": "Insulin resistance → androgen excess → additional DHT-driven sebum production" },
    { "factor": "INF_CHRONIC_001", "description": "Systemic inflammation converts comedones to inflammatory lesions faster" }
  ],
  "dietary_triggers_india": ["Maida roti", "White rice excess", "Sugary chai", "Packaged biscuits/namkeen", "Sweetened lassi", "Mithai"],
  "lab_confirmation": ["LAB_FASTING_INSULIN_001", "LAB_HOMA_IR_001", "LAB_HBA1C_001"],
  "intervention_ref": "INT_INSULIN_ACNE_001"
}

{
  "id": "PATH_OMEGA3_SKIN_001",
  "node_type": "pathway",
  "version": "1.0",
  "name": "Omega-3 Deficiency → Skin Barrier Dysfunction → Dry/Inflamed Skin",
  "root_cause": "Insufficient omega-3 fatty acids → compromised skin lipid barrier → moisture loss and inflammation",
  "terminal_symptom": "SYM_DRYSKIN_001",
  "confidence_base": 0.55,
  "biological_chain": [
    {
      "step": 1,
      "node_ref": "NUT_OMEGA3_001",
      "event": "Dietary omega-3 (EPA, DHA) intake insufficient",
      "mechanism": "Vegetarian diets provide only ALA (flaxseed, walnut) — inefficient conversion to EPA/DHA"
    },
    {
      "step": 2,
      "node_ref": "BIO_EPIDERMIS_001",
      "event": "Skin lipid barrier composition shifts toward pro-inflammatory omega-6 dominance",
      "mechanism": "Omega-3:Omega-6 ratio determines prostaglandin balance. Low omega-3 → PGE2 dominance → inflammation."
    },
    {
      "step": 3,
      "node_ref": "BIO_DERMIS_001",
      "event": "Increased transepidermal water loss (TEWL) — barrier not holding moisture",
      "mechanism": "Omega-3 is structural component of skin cell membranes — membrane fluidity reduced"
    },
    {
      "step": 4,
      "node_ref": "SYM_DRYSKIN_001",
      "event": "Chronic dry, flaky, sensitive skin with low-grade inflammation",
      "mechanism": "Barrier dysfunction + reduced anti-inflammatory prostaglandins"
    }
  ],
  "amplifying_factors": [
    { "factor": "HYD_FLUID_001", "description": "Dehydration compounds barrier dysfunction" },
    { "factor": "ENV_UV_001", "description": "UV damage worsens already-compromised barrier" }
  ],
  "lab_confirmation": null,
  "clinical_assessment": "Dietary history of omega-3 intake + skin presentation sufficient for clinical diagnosis",
  "intervention_ref": "INT_OMEGA3_001"
}

{
  "id": "PATH_THYROID_WEIGHT_001",
  "node_type": "pathway",
  "version": "1.0",
  "name": "Hypothyroidism → Weight Gain Pathway",
  "root_cause": "Low thyroid hormone → reduced basal metabolic rate",
  "terminal_symptom": "SYM_WEIGHTGAIN_001",
  "confidence_base": 0.65,
  "biological_chain": [
    {
      "step": 1,
      "node_ref": "HOR_THYROID_001",
      "event": "T3 levels fall — cells receive insufficient thyroid signal",
      "mechanism": "T3 binds nuclear receptors regulating mitochondrial biogenesis and basal metabolic rate"
    },
    {
      "step": 2,
      "node_ref": "BIO_MITOCHONDRIA_001",
      "event": "Mitochondrial ATP production efficiency decreases",
      "mechanism": "T3 regulates UCP (uncoupling proteins) — thermogenesis reduced → fewer calories burned at rest"
    },
    {
      "step": 3,
      "node_ref": "SYM_WEIGHTGAIN_001",
      "event": "Weight gain despite no change in diet — 2–5 kg typical in hypothyroidism",
      "mechanism": "Reduced BMR + increased water retention (myxoedema) + constipation from slowed gut motility"
    }
  ],
  "distinguishing_from": {
    "PATH_PCOS_HAIR_001": "Thyroid → cold intolerance, constipation, hoarse voice. PCOS → irregular periods, androgen signs.",
    "insulin_resistance": "Both cause weight gain — often concurrent. Check both TSH and fasting insulin."
  },
  "lab_confirmation": ["LAB_TSH_001", "LAB_FT3_001", "LAB_FT4_001"],
  "intervention_ref": "INT_THYROID_001"
}
```

---

---

# MISSING INTERVENTION NODES (29_INTERVENTION_ENGINE continued)

---

```json
{
  "id": "INT_THYROID_001",
  "node_type": "intervention",
  "version": "1.0",
  "name": "Hypothyroidism / Low Thyroid — Intervention Plan",
  "root_cause_ref": "RCE_THYROID_HAIR_001",
  "pathway_ref": "PATH_THYROID_HAIR_001",
  "minimum_confidence_to_fire": 0.55,
  "important_caveat": "Overt hypothyroidism requires medical treatment (levothyroxine). HealthSync addresses nutritional and lifestyle support — not medical treatment replacement.",
  "sections": {
    "nutrition": {
      "thyroid_supporting_nutrients": [
        {
          "nutrient_ref": "NUT_SELENIUM_001",
          "role": "Deiodinase enzyme cofactor — T4 to T3 conversion",
          "source": "1–2 Brazil nuts daily (FOD_BRAZIL_NUT_001) provides full RDA",
          "caution": "Do not exceed 3 Brazil nuts daily — selenium toxicity risk"
        },
        {
          "nutrient_ref": "NUT_IRON_001",
          "role": "Thyroid peroxidase (TPO) enzyme requires iron — iron deficiency impairs T4 synthesis",
          "action": "Check and optimise ferritin alongside thyroid treatment",
          "food_refs": ["FOD_SPINACH_001", "FOD_RAJMA_001", "FOD_SESAME_001"]
        },
        {
          "nutrient": "Iodine",
          "role": "Structural component of T3 and T4 — required for synthesis",
          "source": "Iodised salt (primary). Dairy, eggs.",
          "caution": "Do NOT supplement iodine without testing — excess iodine worsens Hashimoto's autoimmunity"
        },
        {
          "nutrient_ref": "NUT_MAGNESIUM_001",
          "role": "Thyroid hormone receptor function requires magnesium",
          "source_ref": "FOD_PUMPKIN_SEEDS_001"
        },
        {
          "nutrient_ref": "NUT_VITD_001",
          "role": "Vitamin D deficiency increases Hashimoto's autoimmune risk. VDR involved in thyroid cell function.",
          "action": "Check LAB_VITD_001. Target 50–80 ng/mL."
        }
      ],
      "goitrogens_note": {
        "foods": ["Raw cruciferous vegetables (cabbage, cauliflower, broccoli, kale)", "Raw soy"],
        "concern": "Goitrogens block iodine uptake in thyroid. Clinically significant only in iodine-deficient individuals.",
        "advice": "COOKING neutralises 90% of goitrogenic activity. No need to eliminate — cook these vegetables. Do not eat large amounts raw if TSH is elevated."
      },
      "gluten_note": "In Hashimoto's thyroiditis — consider gluten sensitivity evaluation. Molecular mimicry between gliadin and thyroid tissue is established. Trial gluten reduction for 8 weeks if Hashimoto's confirmed."
    },
    "lifestyle": {
      "sleep": {
        "instruction": "Thyroid hormone secretion has circadian rhythm. Regular 10 PM–6 AM sleep pattern supports thyroid recovery.",
        "ref": "SLP_CIRCADIAN_001"
      },
      "stress": {
        "instruction": "Chronic stress elevates cortisol → suppresses TSH production → worsens subclinical hypothyroid.",
        "ref": "STR_CHRONIC_001"
      },
      "exercise": {
        "instruction": "Moderate exercise improves thyroid hormone receptor sensitivity. Avoid excessive high-intensity training — temporarily elevates reverse T3.",
        "ref": "EXE_AEROBIC_001"
      }
    },
    "supplement": {
      "selenium": "200 mcg/day selenomethionine — under supervision for Hashimoto's (reduces anti-TPO antibodies by 40% in studies)",
      "vitamin_d": "2000–4000 IU daily if deficient (ref: LAB_VITD_001)",
      "medical_note": "Levothyroxine (T4) or combination T4+T3 therapy — prescribed only by endocrinologist based on labs"
    },
    "medical_referral": {
      "trigger_conditions": [
        "TSH above 4.0 mIU/L on two tests",
        "FT3 below 2.3 pg/mL",
        "Anti-TPO antibodies elevated (Hashimoto's confirmed)",
        "Symptoms not improving with nutritional support in 3 months"
      ],
      "specialist": "Endocrinologist"
    },
    "hair_specific_note": "Hair recovery from thyroid-related loss requires 6–12 months after TSH normalisation. Hair is last to recover, first to fall. Do not judge thyroid treatment success by hair before 6 months."
  },
  "progress_ref": "PRG_THYROID_001"
}

{
  "id": "INT_DHT_001",
  "node_type": "intervention",
  "version": "1.0",
  "name": "DHT Excess / Androgenetic Alopecia — Intervention Plan",
  "root_cause_ref": "RCE_DHT_HAIR_001",
  "pathway_ref": "PATH_DHT_HAIR_001",
  "minimum_confidence_to_fire": 0.60,
  "important_caveat": "Androgenetic alopecia is genetically determined. Lifestyle intervention slows progression and reduces inflammation but cannot reverse established follicle miniaturisation. Medical treatment (minoxidil, finasteride) may be required.",
  "sections": {
    "nutrition": {
      "dht_inhibiting_nutrients": [
        {
          "nutrient_ref": "NUT_ZINC_001",
          "mechanism": "Inhibits 5-alpha reductase enzyme → less DHT conversion",
          "dose": "25–30 mg/day",
          "food_refs": ["FOD_PUMPKIN_SEEDS_001", "FOD_CASHEW_001", "FOD_CHICKPEA_001"]
        },
        {
          "item": "Green Tea (EGCG)",
          "mechanism": "Catechins inhibit 5-alpha reductase. Reduces DHT locally.",
          "dose": "2–3 cups daily (unsweetened)"
        },
        {
          "item": "Lycopene",
          "mechanism": "Inhibits 5-alpha reductase. Found in tomatoes.",
          "food": "Cooked tomatoes (cooking increases lycopene bioavailability)"
        }
      ],
      "insulin_control": {
        "instruction": "Insulin resistance drives ovarian androgen production. Low-GI diet reduces androgen load.",
        "ref": "BLD_INSULIN_RESISTANCE_001",
        "action": "Reduce maida, white rice, sugar. Increase dal, vegetables, protein at each meal."
      },
      "anti_inflammatory_diet": {
        "instruction": "DHT-mediated inflammation is amplified by systemic inflammation. Anti-inflammatory diet reduces progression.",
        "ref": "INF_CHRONIC_001",
        "foods_ref": "NUT_OMEGA3_001"
      }
    },
    "lifestyle": {
      "stress": {
        "instruction": "Cortisol increases androgen production. Stress management reduces androgen load.",
        "ref": "STR_CHRONIC_001"
      },
      "sleep": {
        "instruction": "Sleep deprivation raises cortisol and reduces insulin sensitivity — both worsen androgen excess.",
        "ref": "SLP_DEEPSLEEP_001"
      },
      "scalp_care": {
        "instruction": "Scalp massage 4 min daily — evidence (2016 study) shows increased hair thickness from mechanical stimulation of dermal papilla.",
        "ref": "BIO_DERMALPAPILLA_001"
      }
    },
    "supplement": {
      "saw_palmetto": "320 mg/day — 5-alpha reductase inhibitor. Evidence-based for androgenetic alopecia. Fewer side effects than finasteride.",
      "zinc": "25 mg zinc picolinate daily",
      "medical_options": {
        "topical_minoxidil": "5% topical minoxidil — first-line medical treatment. Increases follicle blood flow, extends anagen. Requires continued use.",
        "finasteride": "1 mg oral finasteride (males) — prescription only. Reduces DHT by 70%. Side effects in minority.",
        "specialist": "Dermatologist / Trichologist"
      }
    },
    "medical_referral": {
      "trigger_conditions": [
        "Norwood grade III or above (males)",
        "Ludwig grade II or above (females)",
        "Rapid progression within 6 months",
        "No response to nutritional intervention at 6 months"
      ],
      "specialist": "Dermatologist / Trichologist"
    },
    "realistic_expectation": "DHT intervention slows progression and maintains existing hair. True reversal of advanced miniaturisation requires PRP, hair transplant, or sustained medical treatment."
  },
  "progress_ref": "PRG_DHT_001"
}

{
  "id": "INT_VITD_001",
  "node_type": "intervention",
  "version": "1.0",
  "name": "Vitamin D Deficiency — Intervention Plan",
  "root_cause_ref": "RCE_VITD_HAIR_001",
  "pathway_ref": "PATH_VITD_HAIR_001",
  "minimum_confidence_to_fire": 0.50,
  "sections": {
    "sun_exposure": {
      "instruction": "15–20 minutes of direct sunlight between 11 AM and 2 PM on arms and legs (not through glass). 3–4 days per week.",
      "india_note": "Afternoon sun in India provides sufficient UVB. Morning and evening sun (golden hour) has low UVB — inadequate for Vitamin D synthesis.",
      "barriers": ["Dark clothing covering skin", "Sunscreen SPF30+ blocks 95% of UVB", "Indoor office lifestyle"]
    },
    "nutrition": {
      "dietary_sources": [
        { "food_ref": "FOD_FATTY_FISH_001", "note": "Highest dietary source. 2–3 servings/week." },
        { "food_ref": "FOD_EGG_YOLK_001", "note": "Moderate source. Eat whole egg, not just white." }
      ],
      "fat_with_supplement": "Always take Vitamin D supplement with a fat-containing meal (ref: ABS_VITD_001)",
      "magnesium_cofactor": "Magnesium activates Vitamin D — take together (ref: NUT_MAGNESIUM_001)"
    },
    "supplement": {
      "deficient_below_20": "Vitamin D3 60,000 IU weekly for 8 weeks (loading dose), then 2000 IU daily maintenance — under physician guidance",
      "insufficient_20_30": "Vitamin D3 2000–4000 IU daily",
      "form": "D3 (cholecalciferol) — not D2. More effective at raising 25(OH)D levels.",
      "monitoring": "Recheck LAB_VITD_001 at 3 months. Target 50–80 ng/mL."
    },
    "medical_referral": {
      "trigger": "Vitamin D below 12 ng/mL (severe deficiency) — physician supervision for loading doses"
    }
  },
  "progress_ref": "PRG_VITD_001"
}

{
  "id": "INT_B12_001",
  "node_type": "intervention",
  "version": "1.0",
  "name": "Vitamin B12 Deficiency — Intervention Plan",
  "root_cause_ref": "RCE_B12_HAIR_001",
  "pathway_ref": "PATH_B12_HAIR_001",
  "minimum_confidence_to_fire": 0.50,
  "sections": {
    "nutrition": {
      "dietary_sources": [
        { "food_ref": "FOD_EGG_001", "note": "Daily egg consumption. Yolk contains B12." },
        { "food_ref": "FOD_MILK_001", "note": "Dairy is reliable B12 source for lacto-vegetarians" },
        { "food_ref": "FOD_MUTTON_001", "note": "High B12 for non-vegetarians" }
      ],
      "vegetarian_note": "Plant foods contain NO B12. Fortified foods (some nutritional yeast, fortified cereals) provide small amounts. Supplementation is almost always necessary for strict vegetarians."
    },
    "supplement": {
      "deficient_below_200": "Methylcobalamin 1500 mcg daily for 3 months, then 500 mcg maintenance",
      "form_note": "Methylcobalamin preferred over cyanocobalamin — active form, better bioavailability and neural uptake",
      "absorption_issue": "If PPIs or Metformin are cause — sublingual B12 bypasses gut absorption issue",
      "severe_below_100": "Intramuscular B12 injections monthly — physician administered"
    },
    "monitoring": {
      "lab_ref": "LAB_B12_001",
      "frequency": "Recheck at 3 months. Target 400–900 pg/mL.",
      "additional": "Check LAB_HOMOCYSTEINE_001 — normalisation confirms functional improvement"
    },
    "medical_referral": {
      "trigger": "B12 below 100 pg/mL with neurological symptoms — urgent physician referral"
    }
  },
  "progress_ref": "PRG_B12_001"
}

{
  "id": "INT_PROTEIN_001",
  "node_type": "intervention",
  "version": "1.0",
  "name": "Protein Deficiency — Intervention Plan",
  "root_cause_ref": "RCE_PROTEIN_HAIR_001",
  "pathway_ref": "PATH_PROTEIN_HAIR_001",
  "minimum_confidence_to_fire": 0.50,
  "sections": {
    "target_intake": {
      "minimum": "0.8 g per kg body weight per day",
      "optimal_for_hair": "1.2–1.5 g per kg body weight per day",
      "example": "60 kg woman → 72–90 g protein per day minimum"
    },
    "nutrition": {
      "indian_vegetarian_sources": [
        { "food_ref": "FOD_DAL_001", "note": "2 servings/day. Dal + rice = complete protein." },
        { "food_ref": "FOD_PANEER_001", "g_protein_per_100g": 18, "note": "100g paneer daily" },
        { "food_ref": "FOD_CHICKPEA_001", "note": "Chole, hummus, roasted chana as snack" },
        { "food_ref": "FOD_EGG_001", "note": "3 whole eggs/day for non-vegetarian vegetarians" }
      ],
      "meal_distribution": "Distribute protein across 3 meals — body cannot store excess protein. 20–30g per meal is optimal.",
      "complementary_proteins": "Dal + rice or dal + roti = complete amino acid profile covering all essential amino acids"
    },
    "supplement": {
      "condition": "Unable to meet protein target through diet alone",
      "option": "Whey protein (if lacto-vegetarian) or pea protein (vegan) — 20–25g added to smoothie or porridge",
      "timing": "Post-exercise or between meals"
    }
  },
  "progress_ref": "PRG_PROTEIN_001"
}

{
  "id": "INT_POSTPARTUM_001",
  "node_type": "intervention",
  "version": "1.0",
  "name": "Postpartum Hair Loss — Intervention Plan",
  "root_cause_ref": "RCE_POSTPARTUM_HAIR_001",
  "pathway_ref": "PATH_POSTPARTUM_HAIR_001",
  "minimum_confidence_to_fire": 0.80,
  "reassurance_first": true,
  "sections": {
    "reassurance": {
      "message": "Postpartum hair loss is completely normal and affects 40–50% of new mothers. It is not a sign of disease. Your hair WILL fully recover by 9–12 months. The body is resetting after pregnancy.",
      "education": "During pregnancy, elevated estrogen kept more hairs in growth phase than normal. After delivery, estrogen drops and these 'extra' hairs shed together. You are not losing more hair than normal — you are returning to your pre-pregnancy baseline."
    },
    "concurrent_iron_protocol": {
      "instruction": "Simultaneously check and treat iron deficiency — very common concurrent cause",
      "ref": "INT_IRON_001",
      "priority": "HIGH — delivery blood loss + breastfeeding significantly deplete iron"
    },
    "nutrition": {
      "priority_nutrients": [
        { "nutrient_ref": "NUT_PROTEIN_001", "note": "Breastfeeding increases protein need to 71g/day" },
        { "nutrient_ref": "NUT_IRON_001", "note": "Check ferritin. Delivery loses 200–500 mL blood." },
        { "nutrient_ref": "NUT_VITD_001", "note": "Breastfed babies depend on mother's Vitamin D. Supplement 4000 IU/day." },
        { "nutrient_ref": "NUT_B12_001", "note": "Breast milk B12 depends on mother's stores — especially critical for vegetarian mothers" },
        { "nutrient_ref": "NUT_OMEGA3_001", "note": "DHA in breast milk for baby brain development — also supports mother's mood" }
      ]
    },
    "lifestyle": {
      "sleep": {
        "instruction": "Sleep deprivation is unavoidable with newborn. Prioritise 1 consolidated sleep block per 24 hours when possible. Sleep when baby sleeps.",
        "ref": "SLP_DEEPSLEEP_001"
      },
      "stress": {
        "instruction": "Postpartum anxiety is common. High cortisol worsens hair shedding. Partner/family support critical.",
        "ref": "STR_CHRONIC_001"
      }
    },
    "medical_referral": {
      "trigger": "Hair shedding continuing beyond 12 months postpartum — rule out postpartum thyroiditis, iron deficiency anaemia",
      "specialist": "General physician"
    }
  },
  "progress_ref": "PRG_POSTPARTUM_001"
}

{
  "id": "INT_INSULIN_ACNE_001",
  "node_type": "intervention",
  "version": "1.0",
  "name": "Insulin-Driven Acne — Intervention Plan",
  "root_cause_ref": "RCE_INSULIN_ACNE_001",
  "pathway_ref": "PATH_INSULIN_ACNE_001",
  "minimum_confidence_to_fire": 0.55,
  "sections": {
    "nutrition": {
      "strategy": "Low glycaemic index diet — reduce insulin spikes that drive sebum overproduction",
      "reduce": [
        { "item": "Maida-based foods (white bread, biscuits, naan, samosa)", "glycaemic_index": "High (70+)" },
        { "item": "Sugary beverages, packaged juices, sweetened chai", "glycaemic_index": "Very high (80+)" },
        { "item": "White rice large portions", "note": "Reduce portion — replace with more dal and vegetables" },
        { "item": "Dairy (if acne worsens with dairy)", "mechanism": "Dairy contains IGF-1 and whey protein — raises insulin independent of sugar" }
      ],
      "increase": [
        { "food_ref": "FOD_DAL_001", "note": "Low GI. Protein slows glucose absorption." },
        { "item": "Non-starchy vegetables", "note": "Fibre slows glucose absorption, feeds microbiome" },
        { "item": "Apple cider vinegar (1 tsp in water before high-carb meal)", "mechanism": "Reduces post-meal glucose spike by ~20%" }
      ],
      "anti_androgen_foods": [
        { "food_ref": "FOD_PUMPKIN_SEEDS_001", "reason": "Zinc — 5-AR inhibition, reduces DHT-driven sebum" },
        { "item": "Spearmint tea", "mechanism": "Clinical evidence for anti-androgenic effect — reduces free testosterone" },
        { "item": "Green tea (EGCG)", "mechanism": "5-alpha reductase inhibition + anti-inflammatory" }
      ]
    },
    "lifestyle": {
      "exercise": {
        "instruction": "Resistance training improves insulin sensitivity — directly reduces insulin-driven sebum production",
        "ref": "EXE_RESISTANCE_001",
        "frequency": "3x/week minimum"
      },
      "sleep": {
        "instruction": "Sleep deprivation is a major driver of insulin resistance. 7–9 hours non-negotiable for acne control.",
        "ref": "SLP_DEEPSLEEP_001"
      }
    },
    "medical_referral": {
      "trigger": "Moderate-severe acne with confirmed PCOS or insulin resistance",
      "specialist": "Dermatologist + Gynecologist/Endocrinologist"
    }
  },
  "progress_ref": "PRG_ACNE_001"
}

{
  "id": "INT_OMEGA3_001",
  "node_type": "intervention",
  "version": "1.0",
  "name": "Omega-3 Skin Health — Intervention Plan",
  "root_cause_ref": "RCE_OMEGA3_SKIN_001",
  "pathway_ref": "PATH_OMEGA3_SKIN_001",
  "minimum_confidence_to_fire": 0.45,
  "sections": {
    "nutrition": {
      "increase": [
        { "food_ref": "FOD_FLAXSEED_001", "dose": "1 tbsp ground flaxseed daily", "note": "Must be ground — whole seeds pass undigested" },
        { "food_ref": "FOD_WALNUT_001", "dose": "30g (5–6 walnuts) daily" },
        { "food_ref": "FOD_FATTY_FISH_001", "dose": "2 servings per week for non-vegetarians" }
      ],
      "reduce": [
        { "item": "Refined vegetable oils (soybean, sunflower, corn)", "reason": "Very high omega-6 → worsens omega-3:6 ratio → pro-inflammatory" },
        { "item": "Replace with", "alternatives": ["Ghee (traditional, stable fat)", "Cold-pressed mustard oil (contains ALA)", "Coconut oil for cooking"] }
      ]
    },
    "supplement": {
      "vegetarian": "Algae-derived DHA+EPA 250–500 mg daily (bypasses ALA conversion inefficiency)",
      "non_vegetarian": "Fish oil 2g/day EPA+DHA. Take with food.",
      "timing": "With largest meal — fat-soluble, absorption with dietary fat"
    }
  },
  "progress_ref": "PRG_SKIN_001"
}
```

---

---

# ALL REMAINING PROGRESS TRACKERS (30_PROGRESS_ENGINE continued)

---

```json
{
  "id": "PRG_THYROID_001",
  "node_type": "progress_tracker",
  "version": "1.0",
  "intervention_ref": "INT_THYROID_001",
  "root_cause_ref": "RCE_THYROID_HAIR_001",
  "important_note": "Thyroid normalisation takes 6–12 weeks. Hair recovery takes 6–12 months AFTER TSH normalises. Set realistic, staged expectations.",
  "milestones": [
    {
      "week": 6,
      "check": "Has energy and cold intolerance improved?",
      "lab": "LAB_TSH_001",
      "expected": "TSH beginning to normalise if nutrition intervention (selenium, iodine) or medication started",
      "if_no_improvement": "Medical referral — may require levothyroxine"
    },
    {
      "week": 12,
      "check": "Has fatigue significantly improved? Constipation better?",
      "lab": ["LAB_TSH_001", "LAB_FT3_001", "LAB_FT4_001"],
      "expected": "TSH in functional range 1.0–2.5. Systemic symptoms improving."
    },
    {
      "week": 24,
      "check": "Is hair shedding reduced? Skin less dry?",
      "lab": "LAB_TSH_001",
      "expected": "Hair recovery begins once TSH stable. Still early for density improvement."
    },
    {
      "week": 48,
      "check": "Has hair density visibly improved? Overall symptom burden reduced?",
      "lab": ["LAB_TSH_001", "LAB_ANTI_TPO_001"],
      "expected": "Significant improvement if underlying cause addressed. Full hair recovery near."
    }
  ],
  "habit_tracking": ["selenium_foods_daily", "sleep_regular_schedule", "stress_management_practice"],
  "feedback_loop": {
    "no_TSH_improvement_by_12_weeks": "Medical referral mandatory — nutritional support alone insufficient",
    "TSH_normal_but_symptoms_persist": "Check FT3 — may have T4→T3 conversion issue"
  }
}

{
  "id": "PRG_DHT_001",
  "node_type": "progress_tracker",
  "version": "1.0",
  "intervention_ref": "INT_DHT_001",
  "root_cause_ref": "RCE_DHT_HAIR_001",
  "important_note": "Androgenetic alopecia progression is measured in years. Realistic goal is STABILISATION of loss, not reversal. Frame progress accordingly.",
  "milestones": [
    {
      "week": 12,
      "check": "Has rate of hair fall reduced?",
      "lab": ["LAB_FREE_TESTOSTERONE_001", "LAB_SHBG_001"],
      "expected": "Shedding rate should reduce if androgen levels improving"
    },
    {
      "week": 24,
      "check": "Is thinning stable — not progressing further?",
      "visual": "Compare part width photos taken today vs 6 months ago",
      "expected": "Stabilisation is success. Reversal requires medical treatment."
    },
    {
      "week": 36,
      "check": "Any new fine hair growth at recession areas?",
      "expected": "With lifestyle intervention — minimal new growth possible. Stronger result with medical treatment."
    }
  ],
  "habit_tracking": ["low_GI_diet_days", "zinc_supplement_taken", "scalp_massage_minutes_daily", "stress_score"]
}

{
  "id": "PRG_VITD_001",
  "node_type": "progress_tracker",
  "version": "1.0",
  "intervention_ref": "INT_VITD_001",
  "root_cause_ref": "RCE_VITD_HAIR_001",
  "milestones": [
    {
      "week": 8,
      "check": "Do you feel less fatigued and more motivated?",
      "lab": "LAB_VITD_001",
      "expected": "25(OH)D should rise 10–20 ng/mL with supplementation. Mood and energy improve before hair."
    },
    {
      "week": 16,
      "check": "Is hair shedding reducing?",
      "lab": "LAB_VITD_001",
      "expected": "25(OH)D should reach 40+ ng/mL. VDR activation supporting anagen re-entry."
    },
    {
      "week": 24,
      "check": "New hair growth visible?",
      "lab": "LAB_VITD_001",
      "expected": "Target 50–80 ng/mL maintained. New hair density gradually improving."
    }
  ],
  "habit_tracking": ["sun_exposure_minutes_daily", "supplement_taken_with_fat_meal", "lab_done"]
}

{
  "id": "PRG_B12_001",
  "node_type": "progress_tracker",
  "version": "1.0",
  "intervention_ref": "INT_B12_001",
  "root_cause_ref": "RCE_B12_HAIR_001",
  "milestones": [
    {
      "week": 4,
      "check": "Has energy and brain clarity improved?",
      "expected": "B12 neurological effects often improve within 4–6 weeks of supplementation"
    },
    {
      "week": 12,
      "check": "Lab recheck — B12 level in range?",
      "lab": ["LAB_B12_001", "LAB_MCV_001"],
      "expected": "B12 above 400 pg/mL. MCV normalising (was elevated in deficiency)."
    },
    {
      "week": 24,
      "check": "Hair shedding reduced? New growth?",
      "expected": "Hair recovery follows energy improvement by 1–2 months"
    }
  ],
  "habit_tracking": ["supplement_taken_daily", "dietary_B12_sources"]
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
      "check": "Energy levels more stable after meals? Less post-meal crashes?",
      "expected": "First sign of improving insulin sensitivity — stable energy"
    },
    {
      "week": 8,
      "check": "Any improvement in period regularity?",
      "lab": "LAB_FASTING_INSULIN_001",
      "expected": "Fasting insulin reducing. Cycle may begin to regularise."
    },
    {
      "week": 12,
      "check": "Is acne reducing? Hair fall slowing?",
      "lab": ["LAB_FREE_TESTOSTERONE_001", "LAB_DHEAS_001"],
      "expected": "Androgen levels should be trending down with insulin control"
    },
    {
      "week": 24,
      "check": "Periods regular? Acne controlled? Hair density stable?",
      "lab": ["LAB_FASTING_INSULIN_001", "LAB_FREE_TESTOSTERONE_001"],
      "expected": "With sustained effort — significant hormonal rebalancing"
    }
  ],
  "habit_tracking": ["low_GI_meals_daily", "exercise_sessions_per_week", "sleep_hours", "sugar_free_days"],
  "feedback_loop": {
    "no_improvement_12_weeks": "Medical referral. Consider Metformin or inositol under supervision.",
    "regression": "Review diet compliance — single biggest driver is food"
  }
}

{
  "id": "PRG_STRESS_001",
  "node_type": "progress_tracker",
  "version": "1.0",
  "intervention_ref": "INT_STRESS_001",
  "root_cause_ref": "RCE_CORTISOL_HAIR_001",
  "important_note": "Stress-related hair loss has a 2–3 month lag. Shedding started 2–3 months after the stress began. Recovery also lags. Hair improvement begins 2–3 months after stress is managed.",
  "milestones": [
    {
      "week": 4,
      "check": "Is sleep quality improving? Mood more stable?",
      "expected": "Primary indicators of cortisol regulation"
    },
    {
      "week": 8,
      "check": "Subjective stress level reduced (1–10 scale)?",
      "expected": "Cortisol reducing. Hair still shedding — normal at this stage."
    },
    {
      "week": 12,
      "check": "Has daily hair fall count reduced noticeably?",
      "lab": "LAB_MORNING_CORTISOL_001",
      "expected": "Shedding should be reducing now"
    },
    {
      "week": 20,
      "check": "New hair growth visible?",
      "expected": "New fine hairs at hairline. Density beginning to return."
    }
  ],
  "habit_tracking": ["meditation_minutes_daily", "sleep_hours", "caffeine_cutoff_respected", "stress_level_score"]
}

{
  "id": "PRG_GUT_001",
  "node_type": "progress_tracker",
  "version": "1.0",
  "intervention_ref": "INT_GUT_001",
  "root_cause_ref": "RCE_DYSBIOSIS_GUT_001",
  "milestones": [
    {
      "week": 2,
      "check": "Has bloating reduced after meals?",
      "expected": "First and fastest response to gut intervention"
    },
    {
      "week": 4,
      "check": "Is digestion more regular? Less discomfort?",
      "expected": "Microbiome beginning to diversify"
    },
    {
      "week": 8,
      "check": "Is skin clearer? Energy improving?",
      "expected": "Gut-skin axis improvement. Systemic inflammation reducing."
    },
    {
      "week": 12,
      "check": "Hair fall reducing? Skin significantly clearer?",
      "expected": "Nutrient absorption improving — downstream effects on hair and skin visible"
    }
  ],
  "habit_tracking": ["fermented_food_servings_daily", "fibre_servings_daily", "plant_variety_per_week", "stress_management"]
}

{
  "id": "PRG_PROTEIN_001",
  "node_type": "progress_tracker",
  "version": "1.0",
  "intervention_ref": "INT_PROTEIN_001",
  "root_cause_ref": "RCE_PROTEIN_HAIR_001",
  "milestones": [
    {
      "week": 4,
      "check": "Are you meeting protein target daily (check via food log)?",
      "expected": "Dietary compliance is the only measure at this stage"
    },
    {
      "week": 8,
      "check": "Is hair shaft feeling stronger? Less breakage?",
      "expected": "Keratin quality improving — hair feels thicker and more resistant"
    },
    {
      "week": 12,
      "check": "Is shedding reduced?",
      "expected": "Telogen effluvium resolving as protein stores replenished"
    },
    {
      "week": 20,
      "check": "New hair growth visible?",
      "expected": "Full thickness hair returning"
    }
  ],
  "habit_tracking": ["protein_grams_daily", "dal_servings_daily", "egg_or_dairy_intake"]
}

{
  "id": "PRG_POSTPARTUM_001",
  "node_type": "progress_tracker",
  "version": "1.0",
  "intervention_ref": "INT_POSTPARTUM_001",
  "milestones": [
    {
      "week": 4,
      "check": "Reassurance check — is mother aware this is normal and temporary?",
      "expected": "Education and reassurance are primary interventions"
    },
    {
      "week": 8,
      "check": "Is ferritin checked and iron intervention started if needed?",
      "lab": "LAB_FERRITIN_001",
      "expected": "Concurrent iron deficiency treated simultaneously"
    },
    {
      "month": 6,
      "check": "Is shedding significantly reduced?",
      "expected": "Peak shedding should be past. Recovery phase beginning."
    },
    {
      "month": 9,
      "check": "Is hair density returning to pre-pregnancy baseline?",
      "expected": "Near-complete recovery for most women",
      "if_not_improving": "Check LAB_TSH_001 — postpartum thyroiditis may be concurrent"
    },
    {
      "month": 12,
      "check": "Full recovery?",
      "expected": "Complete recovery. If not — investigate persistent causes."
    }
  ],
  "habit_tracking": ["iron_protocol_followed", "protein_intake_adequate", "sleep_quality"]
}

{
  "id": "PRG_ACNE_001",
  "node_type": "progress_tracker",
  "version": "1.0",
  "intervention_ref": "INT_INSULIN_ACNE_001",
  "milestones": [
    {
      "week": 2,
      "check": "New breakouts reducing in frequency?",
      "expected": "Low-GI diet begins impacting insulin within days"
    },
    {
      "week": 4,
      "check": "Active acne count reducing?",
      "expected": "Significant reduction in new lesions. Old lesions healing."
    },
    {
      "week": 8,
      "check": "Skin significantly clearer?",
      "lab": "LAB_FASTING_INSULIN_001",
      "expected": "Insulin normalising. Sebum production reducing."
    },
    {
      "week": 12,
      "check": "Are breakouts rare and mild only?",
      "expected": "Dietary and lifestyle causes substantially controlled"
    }
  ],
  "habit_tracking": ["low_GI_diet_compliance", "dairy_intake", "sugar_intake", "exercise_sessions"]
}

{
  "id": "PRG_SKIN_001",
  "node_type": "progress_tracker",
  "version": "1.0",
  "intervention_ref": "INT_OMEGA3_001",
  "milestones": [
    {
      "week": 4,
      "check": "Is skin feeling less tight or dry?",
      "expected": "Omega-3 incorporation into skin cell membranes begins"
    },
    {
      "week": 8,
      "check": "Skin hydration and smoothness improved?",
      "expected": "Barrier function visibly improving"
    },
    {
      "week": 12,
      "check": "Inflammatory skin symptoms (redness, flakiness) reducing?",
      "expected": "Anti-inflammatory effects measurable at 12 weeks"
    }
  ],
  "habit_tracking": ["omega3_supplement_daily", "cooking_oil_switched", "flaxseed_added_to_diet"]
}
```

---

---

# COMPLETE NODE REGISTRY

## All Nodes Across All 30 Layers

### 01_SYSTEMS (10 nodes)
| Node ID | Name |
|---------|------|
| `SYS_HAIR_001` | Hair System |
| `SYS_SKIN_001` | Skin System |
| `SYS_ENERGY_001` | Energy System |
| `SYS_HORMONAL_001` | Hormonal System |
| `SYS_DIGESTIVE_001` | Digestive System |
| `SYS_METABOLIC_001` | Metabolic System |
| `SYS_SLEEP_001` | Sleep System |
| `SYS_MUSCULOSKELETAL_001` | Musculoskeletal System |
| `SYS_CARDIOMETABOLIC_001` | Cardiometabolic System |
| `SYS_WEIGHT_001` | Weight Regulation System |

### 02_BIOLOGY (15 nodes)
| Node ID | Structure |
|---------|-----------|
| `BIO_FOLLICLE_001` | Hair Follicle |
| `BIO_DERMALPAPILLA_001` | Dermal Papilla |
| `BIO_HAIRBULB_001` | Hair Bulb |
| `BIO_MATRIX_001` | Hair Matrix |
| `BIO_EPIDERMIS_001` | Epidermis |
| `BIO_DERMIS_001` | Dermis |
| `BIO_COLLAGEN_001` | Collagen Network |
| `BIO_SEBGLAND_001` | Sebaceous Gland |
| `BIO_MITOCHONDRIA_001` | Mitochondria |
| `BIO_THYROID_001` | Thyroid Gland |
| `BIO_MICROBIOME_001` | Gut Microbiome |
| `BIO_GUTLINING_001` | Intestinal Epithelial Lining |
| `BIO_ADRENAL_001` | Adrenal Glands |
| `BIO_ETC_001` | Electron Transport Chain |
| `BIO_PANCREAS_001` | Pancreas |

### 03_SYMPTOMS (12 nodes)
| Node ID | Symptom |
|---------|---------|
| `SYM_HAIRFALL_001` | Hair Fall |
| `SYM_HAIRTHIN_001` | Hair Thinning |
| `SYM_ACNE_001` | Acne |
| `SYM_DRYSKIN_001` | Dry Skin |
| `SYM_OILYSKIN_001` | Oily Skin |
| `SYM_DARKSPOTS_001` | Dark Spots |
| `SYM_FATIGUE_001` | Fatigue |
| `SYM_BRAINFOG_001` | Brain Fog |
| `SYM_LOWENERGY_001` | Low Energy |
| `SYM_WEIGHTGAIN_001` | Unexplained Weight Gain |
| `SYM_POORSLEEP_001` | Poor Sleep |
| `SYM_BLOATING_001` | Bloating |
| `SYM_IRREGULARPERIODS_001` | Irregular Periods |
| `SYM_SCALPDRY_001` | Dry Scalp |

### 04_NUTRITION (12 nodes)
| Node ID | Nutrient |
|---------|----------|
| `NUT_IRON_001` | Iron |
| `NUT_ZINC_001` | Zinc |
| `NUT_VITD_001` | Vitamin D |
| `NUT_B12_001` | Vitamin B12 |
| `NUT_PROTEIN_001` | Protein |
| `NUT_OMEGA3_001` | Omega-3 Fatty Acids |
| `NUT_MAGNESIUM_001` | Magnesium |
| `NUT_SELENIUM_001` | Selenium |
| `NUT_BIOTIN_001` | Biotin |
| `NUT_VITC_001` | Vitamin C |
| `NUT_FOLATE_001` | Folate |
| `NUT_IODINE_001` | Iodine |
| `NUT_COENZYME_001` | Coenzyme Q10 |
| `NUT_COPPER_001` | Copper |
| `NUT_CALCIUM_001` | Calcium |

### 05_ABSORPTION (5 nodes)
| Node ID | Nutrient |
|---------|----------|
| `ABS_IRON_001` | Iron Absorption |
| `ABS_B12_001` | B12 Absorption |
| `ABS_ZINC_001` | Zinc Absorption |
| `ABS_VITD_001` | Vitamin D Absorption |
| `ABS_OMEGA3_001` | Omega-3 Absorption |

### 06_GUT_HEALTH (4 nodes)
| Node ID | Condition |
|---------|-----------|
| `GUT_DYSBIOSIS_001` | Dysbiosis |
| `GUT_LEAKYGUT_001` | Leaky Gut / Increased Permeability |
| `GUT_MALABSORPTION_001` | Nutrient Malabsorption |
| `GUT_IBS_001` | Irritable Bowel Syndrome |

### 07_HORMONES (10 nodes)
| Node ID | Hormone |
|---------|---------|
| `HOR_DHT_001` | DHT |
| `HOR_CORTISOL_001` | Cortisol |
| `HOR_INSULIN_001` | Insulin |
| `HOR_THYROID_001` | Thyroid Hormones T3/T4 |
| `HOR_ESTROGEN_001` | Estrogen |
| `HOR_IGF1_001` | IGF-1 |
| `HOR_MELATONIN_001` | Melatonin |
| `HOR_GH_001` | Growth Hormone |
| `HOR_LEPTIN_001` | Leptin |
| `HOR_LH_001` | Luteinising Hormone |
| `HOR_ADRENALINE_001` | Adrenaline |
| `HOR_DHEA_001` | DHEA |
| `HOR_TESTOSTERONE_001` | Testosterone |

### 08_SLEEP (3 nodes)
| Node ID | Topic |
|---------|-------|
| `SLP_BIOLOGY_001` | Sleep Biology Overview |
| `SLP_CIRCADIAN_001` | Circadian Rhythm |
| `SLP_DEEPSLEEP_001` | Deep Sleep / N3 |

### 09_STRESS (2 nodes)
| Node ID | Type |
|---------|------|
| `STR_ACUTE_001` | Acute Stress |
| `STR_CHRONIC_001` | Chronic Stress |

### 10_EXERCISE (2 nodes)
| Node ID | Type |
|---------|------|
| `EXE_RESISTANCE_001` | Resistance Training |
| `EXE_AEROBIC_001` | Aerobic Exercise |

### 11_RECOVERY (2 nodes)
| Node ID | Tissue |
|---------|--------|
| `REC_FOLLICLE_001` | Hair Follicle Recovery |
| `REC_SKIN_001` | Skin Recovery |

### 12_INFLAMMATION (2 nodes)
| Node ID | Type |
|---------|------|
| `INF_ACUTE_001` | Acute Inflammation |
| `INF_CHRONIC_001` | Chronic Low-Grade Inflammation |

### 13_OXIDATIVE_STRESS (1 node)
| Node ID | Topic |
|---------|-------|
| `OXI_FREE_RADICAL_001` | Free Radicals and Oxidative Stress |

### 14_BLOOD_SUGAR (2 nodes)
| Node ID | Condition |
|---------|-----------|
| `BLD_INSULIN_RESISTANCE_001` | Insulin Resistance |
| `BLD_PREDIABETES_001` | Prediabetes |
| `BLD_DIABETES_001` | Type 2 Diabetes |

### 15_HYDRATION (1 node)
| Node ID | Topic |
|---------|-------|
| `HYD_FLUID_001` | Fluid Balance and Hydration |

### 16_ENVIRONMENT (3 nodes)
| Node ID | Stressor |
|---------|----------|
| `ENV_HARDWATER_001` | Hard Water |
| `ENV_UV_001` | UV Exposure |
| `ENV_POLLUTION_001` | Air Pollution |
| `ENV_HEAT_001` | Heat / Styling Damage |

### 17_MEDICAL_CONDITIONS (6 nodes)
| Node ID | Condition |
|---------|-----------|
| `MED_PCOS_001` | PCOS |
| `MED_HYPOTHYROID_001` | Hypothyroidism |
| `MED_ANEMIA_001` | Iron Deficiency Anaemia |
| `MED_HASHIMOTOS_001` | Hashimoto's Thyroiditis |
| `MED_ALOPECIA_001` | Alopecia Areata |
| `MED_CELIAC_001` | Celiac Disease |
| `MED_DIABETES_001` | Type 2 Diabetes |

### 18_MEDICATIONS (4 nodes)
| Node ID | Medication |
|---------|------------|
| `MEDS_PPIS_001` | Proton Pump Inhibitors |
| `MEDS_METFORMIN_001` | Metformin |
| `MEDS_OCP_001` | Oral Contraceptive Pills |
| `MEDS_ANTIBIOTICS_001` | Antibiotics |

### 19_GENETICS (3 nodes)
| Node ID | Topic |
|---------|-------|
| `GEN_ANDROGEN_SENSITIVITY_001` | Androgen Receptor Sensitivity |
| `GEN_MTHFR_001` | MTHFR Gene Variant |
| `GEN_THYROID_AUTOIMMUNE_001` | Thyroid Autoimmune Predisposition |

### 20_LIFE_STAGES (5 nodes)
| Node ID | Stage |
|---------|-------|
| `LIF_PREGNANCY_001` | Pregnancy |
| `LIF_POSTPARTUM_001` | Postpartum |
| `LIF_MENOPAUSE_001` | Menopause |
| `LIF_ADOLESCENCE_001` | Adolescence |
| `LIF_AGING_001` | Aging (50+) |

### 21_FOOD_DATABASE (20+ nodes)
| Node ID | Food |
|---------|------|
| `FOD_SPINACH_001` | Palak (Spinach) |
| `FOD_RAJMA_001` | Rajma (Kidney Beans) |
| `FOD_JAGGERY_001` | Jaggery |
| `FOD_AMLA_001` | Amla |
| `FOD_SESAME_001` | Til (Sesame Seeds) |
| `FOD_PUMPKIN_SEEDS_001` | Kaddu ke Beej |
| `FOD_DAL_001` | Dal (Lentils) |
| `FOD_PANEER_001` | Paneer |
| `FOD_EGG_001` | Eggs |
| `FOD_EGG_YOLK_001` | Egg Yolk |
| `FOD_MILK_001` | Milk |
| `FOD_MUTTON_001` | Mutton |
| `FOD_CHICKEN_LIVER_001` | Chicken Liver |
| `FOD_FATTY_FISH_001` | Fatty Fish (Mackerel/Salmon) |
| `FOD_BANANA_001` | Banana |
| `FOD_GUAVA_001` | Guava |
| `FOD_LEMON_001` | Lemon |
| `FOD_WALNUT_001` | Walnut |
| `FOD_FLAXSEED_001` | Flaxseed (Alsi) |
| `FOD_CASHEW_001` | Cashew |
| `FOD_CHICKPEA_001` | Chana / Chickpea |
| `FOD_BRAZIL_NUT_001` | Brazil Nuts |
| `FOD_PEANUT_001` | Peanuts |
| `FOD_POMEGRANATE_001` | Anar (Pomegranate) |

### 22_LAB_MARKERS (18 nodes)
| Node ID | Test |
|---------|------|
| `LAB_FERRITIN_001` | Serum Ferritin |
| `LAB_SERUM_IRON_001` | Serum Iron |
| `LAB_TIBC_001` | TIBC |
| `LAB_TRANSFERRIN_001` | Transferrin |
| `LAB_CBC_001` | Complete Blood Count |
| `LAB_HB_001` | Haemoglobin |
| `LAB_MCV_001` | Mean Corpuscular Volume |
| `LAB_TSH_001` | TSH |
| `LAB_FT3_001` | Free T3 |
| `LAB_FT4_001` | Free T4 |
| `LAB_ANTI_TPO_001` | Anti-TPO Antibodies |
| `LAB_VITD_001` | 25-Hydroxy Vitamin D |
| `LAB_B12_001` | Serum Vitamin B12 |
| `LAB_HOMOCYSTEINE_001` | Homocysteine |
| `LAB_HBA1C_001` | HbA1c |
| `LAB_FASTING_GLUCOSE_001` | Fasting Glucose |
| `LAB_FASTING_INSULIN_001` | Fasting Insulin |
| `LAB_HOMA_IR_001` | HOMA-IR |
| `LAB_FREE_TESTOSTERONE_001` | Free Testosterone |
| `LAB_TOTAL_TESTOSTERONE_001` | Total Testosterone |
| `LAB_SHBG_001` | SHBG |
| `LAB_DHEAS_001` | DHEAS |
| `LAB_LH_FSH_RATIO_001` | LH:FSH Ratio |
| `LAB_ESTRADIOL_001` | Estradiol (E2) |
| `LAB_FSH_001` | FSH |
| `LAB_CRP_001` | hs-CRP |
| `LAB_SERUM_ZINC_001` | Serum Zinc |
| `LAB_SERUM_MAGNESIUM_001` | Serum Magnesium |
| `LAB_SERUM_ALBUMIN_001` | Serum Albumin |
| `LAB_TOTAL_PROTEIN_001` | Total Serum Protein |
| `LAB_MORNING_CORTISOL_001` | Morning Cortisol |
| `LAB_DHEA_001` | DHEA |
| `LAB_SERUM_SELENIUM_001` | Serum Selenium |

### 23_PATHWAYS (9 nodes)
| Node ID | Pathway |
|---------|---------|
| `PATH_IRON_HAIR_001` | Iron Deficiency → Hair Loss |
| `PATH_DHT_HAIR_001` | DHT Excess → Androgenetic Alopecia |
| `PATH_THYROID_HAIR_001` | Hypothyroidism → Hair Loss |
| `PATH_PCOS_HAIR_001` | PCOS → Hair Loss |
| `PATH_CORTISOL_HAIR_001` | Chronic Stress → Hair Loss |
| `PATH_VITD_HAIR_001` | Vitamin D Deficiency → Hair Loss |
| `PATH_PROTEIN_HAIR_001` | Protein Deficiency → Hair Loss |
| `PATH_B12_HAIR_001` | B12 Deficiency → Hair Loss |
| `PATH_POSTPARTUM_HAIR_001` | Postpartum Telogen Effluvium |
| `PATH_GUT_ACNE_001` | Gut Dysbiosis → Acne |
| `PATH_INSULIN_ACNE_001` | Insulin Resistance → Acne |
| `PATH_OMEGA3_SKIN_001` | Omega-3 Deficiency → Dry Skin |
| `PATH_THYROID_WEIGHT_001` | Hypothyroidism → Weight Gain |

### 24_AI_QUESTIONS (3 nodes)
| Node ID | Trigger |
|---------|---------|
| `AIQ_HAIRFALL_001` | Hair Fall Questions |
| `AIQ_ACNE_001` | Acne Questions |
| `AIQ_FATIGUE_001` | Fatigue / Energy Questions |

### 25_DECISION_ENGINE (5 nodes)
| Node ID | Rule |
|---------|------|
| `DEC_HAIRFALL_FATIGUE_001` | Hair Fall + Fatigue → Iron + Thyroid |
| `DEC_PCOS_CLUSTER_001` | Hair + Acne + Periods → PCOS |
| `DEC_POSTPARTUM_001` | Post-Delivery Hair Fall |
| `DEC_ACNE_HORMONAL_001` | Hormonal Acne Routing |
| `DEC_FATIGUE_ONLY_001` | Fatigue Without Hair Fall |

### 26_ROOT_CAUSE_ENGINE (10 nodes)
| Node ID | Root Cause |
|---------|------------|
| `RCE_IRON_HAIR_001` | Iron Deficiency → Hair |
| `RCE_DHT_HAIR_001` | DHT → Hair |
| `RCE_THYROID_HAIR_001` | Thyroid → Hair |
| `RCE_PCOS_001` | PCOS |
| `RCE_CORTISOL_HAIR_001` | Cortisol → Hair |
| `RCE_VITD_HAIR_001` | Vitamin D → Hair |
| `RCE_PROTEIN_HAIR_001` | Protein → Hair |
| `RCE_B12_HAIR_001` | B12 → Hair |
| `RCE_POSTPARTUM_HAIR_001` | Postpartum → Hair |
| `RCE_DYSBIOSIS_GUT_001` | Dysbiosis → Gut-Skin |
| `RCE_INSULIN_ACNE_001` | Insulin → Acne |
| `RCE_OMEGA3_SKIN_001` | Omega-3 → Skin |
| `RCE_IRON_ENERGY_001` | Iron → Energy/Fatigue |
| `RCE_THYROID_ENERGY_001` | Thyroid → Energy |
| `RCE_B12_ENERGY_001` | B12 → Energy |

### 27_SYMPTOM_CLUSTERS (4 nodes)
| Node ID | Cluster |
|---------|---------|
| `SCL_IRON_001` | Iron Deficiency Cluster |
| `SCL_PCOS_001` | PCOS Cluster |
| `SCL_THYROID_001` | Hypothyroid Cluster |
| `SCL_STRESS_001` | Stress/Cortisol Cluster |

### 28_CONFIDENCE_ENGINE (2 nodes)
| Node ID | Type |
|---------|------|
| `CON_SCHEMA_001` | Output Schema |
| `CON_EXAMPLE_001` | Example Result |

### 29_INTERVENTION_ENGINE (12 nodes)
| Node ID | Intervention |
|---------|-------------|
| `INT_IRON_001` | Iron Deficiency |
| `INT_PCOS_001` | PCOS |
| `INT_THYROID_001` | Thyroid |
| `INT_DHT_001` | DHT / Androgenetic Alopecia |
| `INT_STRESS_001` | Chronic Stress |
| `INT_GUT_001` | Gut Health |
| `INT_VITD_001` | Vitamin D |
| `INT_B12_001` | Vitamin B12 |
| `INT_PROTEIN_001` | Protein Deficiency |
| `INT_POSTPARTUM_001` | Postpartum Hair Loss |
| `INT_INSULIN_ACNE_001` | Insulin-Driven Acne |
| `INT_OMEGA3_001` | Omega-3 / Skin |

### 30_PROGRESS_ENGINE (12 nodes)
| Node ID | Tracks |
|---------|--------|
| `PRG_IRON_001` | Iron intervention |
| `PRG_PCOS_001` | PCOS intervention |
| `PRG_THYROID_001` | Thyroid intervention |
| `PRG_DHT_001` | DHT intervention |
| `PRG_STRESS_001` | Stress intervention |
| `PRG_GUT_001` | Gut intervention |
| `PRG_VITD_001` | Vitamin D intervention |
| `PRG_B12_001` | B12 intervention |
| `PRG_PROTEIN_001` | Protein intervention |
| `PRG_POSTPARTUM_001` | Postpartum intervention |
| `PRG_ACNE_001` | Acne intervention |
| `PRG_SKIN_001` | Omega-3/Skin intervention |

---

**Total nodes defined across all 30 layers: ~210 nodes**

---

---

# CROSS-REFERENCE VALIDATION RULES

These rules are enforced at data entry time to prevent broken references.

```
RULE 01: Every node in PATH_ must have all step.node_ref IDs pointing to
         existing BIO_, NUT_, HOR_, SYM_ nodes.

RULE 02: Every RCE_ node must have a pathway_ref pointing to an existing PATH_ node.

RULE 03: Every INT_ node must have a root_cause_ref pointing to an existing RCE_ node
         AND a pathway_ref pointing to an existing PATH_ node.

RULE 04: Every PRG_ node must have an intervention_ref pointing to an existing INT_ node.

RULE 05: Every SCL_ node must have a root_cause_ref pointing to an existing RCE_ node.

RULE 06: Every DEC_ node must reference existing SYM_ IDs in trigger_conditions
         and existing PATH_ IDs in pathways_loaded.

RULE 07: Every NUT_ node must have an absorption_ref pointing to an existing ABS_ node.

RULE 08: Every SYM_ node must have all root_cause_refs pointing to existing RCE_ nodes.

RULE 09: Every FOD_ node must have all nutrient_refs pointing to existing NUT_ nodes.

RULE 10: Every LAB_ node must have a nutrition_ref or hormone_ref pointing to the
         relevant NUT_ or HOR_ node.
```

---

---

# DEVELOPER IMPLEMENTATION GUIDE

## Phase 1 — Foundation (Week 1–2)
Build the complete Iron pathway end-to-end:
```
NUT_IRON_001 → ABS_IRON_001 → BIO_MATRIX_001 → BIO_FOLLICLE_001
→ SYM_HAIRFALL_001 → PATH_IRON_HAIR_001 → SCL_IRON_001
→ AIQ_HAIRFALL_001 → DEC_HAIRFALL_FATIGUE_001 → RCE_IRON_HAIR_001
→ CON_SCHEMA_001 → INT_IRON_001 → PRG_IRON_001
```
**Validate:** Run a test query: "I have hair fall, I'm vegetarian, I drink chai with meals" — confirm the system outputs INT_IRON_001 with correct food recommendations.

## Phase 2 — Expand Reasoning (Week 3–4)
Add PCOS and Thyroid pathways. Test symptom cluster discrimination:
- "Hair fall + fatigue" → should NOT fire PCOS
- "Hair fall + acne + irregular periods" → should fire PCOS
- "Hair fall + cold intolerance + weight gain" → should fire Thyroid

## Phase 3 — Expand Knowledge (Week 5–6)
Complete all remaining nodes in Layers 1–1.5. Validate cross-references (RULE 01–10).

## Phase 4 — Accuracy Tuning (Week 7–8)
- Test edge cases: two concurrent causes (Iron + Thyroid)
- Test uncertainty flagging: confidence within 0.15 → confirm labs recommended
- Test hallucination guard: confirm no response references non-existent node IDs

## Data Storage Format Options

| Option | Use Case | Trade-off |
|--------|----------|-----------|
| JSON files per layer | Simple start, human-readable | Hard to query across layers |
| SQLite + JSON columns | Mid-scale | Easy local development |
| PostgreSQL + pgvector | Production RAG | Full vector + relational |
| Neo4j (Graph DB) | Ideal for this graph structure | More setup cost |

## RAG Retrieval Strategy

```
Query arrives
    ↓
NLP extracts symptoms → match to SYM_ nodes
    ↓
Vector similarity search on SCL_ nodes (symptom clusters)
    ↓
Load matched PATH_ nodes (biological chains — small, dense, accurate)
    ↓
Load referenced BIO_, NUT_, HOR_ nodes (only what the pathway needs)
    ↓
Load RCE_ → CON_ → INT_ → FOD_ nodes for response assembly
    ↓
Response cites node_refs — hallucination impossible
```

> [!IMPORTANT]
> **Never embed full BIO_ or NUT_ node content in the prompt as free text.** Always pass them as structured references. The AI reads the chain and assembles — it does not summarise from memory.

> [!TIP]
> **Start with 3 pathways (Iron, Thyroid, PCOS) fully implemented and validated** before adding more. A 3-pathway system that is 100% accurate is more valuable than a 30-pathway system with hallucinations.
