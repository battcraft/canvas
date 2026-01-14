---
name: product-description
description: Generate comprehensive product descriptions for ZAZEN SYSTEMS cold chain products. Creates structured descriptions with problem statement, solution overview, technical specifications, applications, and competitive differentiation. Use when launching new products, updating SKUs, or creating marketing collateral.
---

# Product Description Skill

## Purpose

Generate complete, technically accurate, and persuasive product descriptions for ZAZEN SYSTEMS' Intelligence-First Cold Chain Platform products.

## When to Use

- Launching new product SKUs (Motion-Pro, Industrial-Smart, Titan series)
- Updating existing product pages with new features
- Creating sales collateral and specification sheets
- Writing catalog content for distributors
- Preparing product launch materials

## Instructions

### 1. Load Context

Before writing, read:
- **Product specifications**: `/home/user/canvas/.claude/knowledge/products/[product-name].json`
- **Voice DNA**: `/home/user/canvas/.claude/context/voice-dna.json`
- **Target ICP**: `/home/user/canvas/.claude/context/icp.json` (relevant segment)
- **Competitive positioning**: `/home/user/canvas/.claude/knowledge/competitors/comparison.json`

### 2. Structure

Use this proven structure:

```
# [Product Name] — [One-line positioning]

## The Problem
- Specific pain points for target ICP (quantified)
- Why traditional solutions fail
- Cost of inaction (₹ amounts, time waste, risk)

## The Solution
- How this product solves the problem uniquely
- Key technologies with business value (not feature dumping)
- Intelligence features (Gemini cloud + Edge AI)

## Technical Specifications
[TABLE FORMAT]
- Physical specifications (dimensions, weight, capacity)
- Electrical specifications (voltage, power, efficiency)
- Performance specifications (temperature range, cooling capacity)
- Intelligence specifications (prediction windows, sensor suite)
- Compliance certifications (WHO PQS, ISO 9001, BIS)

## Intelligence Features
- Predictive maintenance (with confidence intervals)
- Autonomous optimization (specific algorithms)
- Fleet orchestration (if applicable)
- Integration capabilities (API, ERP, IoT platforms)

## Ideal Applications
[BULLETED LIST]
- Primary use case (industry, scale, pain point)
- Secondary use case
- Tertiary use case
- Anti-pattern (when NOT to use this product)

## Competitive Differentiation
[COMPARISON TABLE]
- vs. Traditional commercial freezers
- vs. IoT monitoring startups
- vs. Premium international brands
(Focus on objective differences, not bashing)

## Pricing & ROI
- Product price range (with context for variants)
- Total cost of ownership (TCO) comparison
- Expected ROI/payback period (for retrofits)
- Subscription tier recommendations

## Installation & Support
- Installation timeline (zero-touch commissioning process)
- Required infrastructure (power, network, space)
- Support options (ZZ-CARE plans)
- Training requirements (HMI orientation, operator certification)

## Call to Action
- Next step for prospect (demo, ROI calculator, contact sales)
```

### 3. Writing Guidelines

**Voice & Tone**:
- Technical depth = 8/10 (precise but accessible)
- Confidence level = 7/10 (category creator, not arrogant)
- Problem-first storytelling (lead with pain, not features)
- Data-driven claims (always include metrics)

**Vocabulary**:
- ✅ Use: "Intelligence-First", "EV-grade", "Predictive maintenance", "Fleet orchestration", "Thermal inertia modeling"
- ❌ Avoid: "Revolutionary", "Disruptive", "Game-changer", "Seamless", "Robust"

**Technical Accuracy**:
- Verify all specs against product datasheets
- Use correct units (kW, RPM, GWP, L, m³, °C, ±0.5°C)
- Include model numbers (ZF-500M, ZT-298, etc.)
- Cite certifications accurately (WHO-E003, ISO 9001)

**Business Credibility**:
- Always quantify savings (25-40%, ₹3.1L/year, 18-month ROI)
- Compare to baseline ("vs. traditional fixed-speed compressors")
- Acknowledge trade-offs ("Not ideal for single-unit retail")
- Include real use cases by industry

### 4. Length Guidelines

- **Flagship products** (ZF-500M, ZF-1388S, ZT-298): 1200-1800 words
- **Variant products** (ZF-300M, ZF-828S): 800-1200 words
- **Retrofit kits**: 1000-1400 words
- **Bundle packages**: 600-900 words

### 5. Quality Checklist

Before delivering:
- [ ] All technical specs verified against product datasheet
- [ ] Voice consistency (technical depth 8, confidence 7, formality 6)
- [ ] ICP-specific pain points addressed with quantification
- [ ] Competitive comparison table included (3 comparisons minimum)
- [ ] ROI metrics included (payback period, annual savings, TCO)
- [ ] Anti-pattern section (when NOT to use product)
- [ ] Removed filler words (robust, seamless, cutting-edge, leverage)
- [ ] Varied sentence structure (5-word punchy + 20-word detailed)
- [ ] Included specific model numbers and certifications
- [ ] Read aloud test passed (sounds natural when spoken)

## Examples

### Example 1: Motion-Pro Series Product Description

**Opening (Problem)**:
"Mobile cold chain operators face a hidden 8-12% efficiency penalty: inverter losses. Every time you convert vehicle DC power to AC for a traditional compressor, then back to DC for control systems, you're burning fuel for nothing. Food trucks lose ₹40,000-₹65,000 annually to this invisible waste. Worse, fixed-speed compressors cycle on-off constantly during transit, creating temperature swings that accelerate product degradation and shorten shelf life."

**Solution**:
"The ZF-500M eliminates inverter losses with native 12-48V DC operation, directly connecting to vehicle batteries or solar arrays. Variable-speed BLDC compressor (2000-3500 RPM) modulates continuously based on thermal load, eliminating wasteful on-off cycling. GPS-aware pre-loading uses route data to maximize thermal capacity before hot loading zones—your freezer intelligently pre-cools 30 minutes before you reach the ice cream parlor pickup, minimizing door-open temperature recovery time."

**Anti-pattern**:
"Not ideal for stationary retail locations with reliable AC power—consider Industrial-Smart Series (ZF-628S to ZF-1388S) for better economics in non-mobile applications."

### Example 2: Industrial-Smart Series Competitive Differentiation

| Feature | Traditional (Blue Star, Voltas) | IoT Monitoring Startups | **ZAZEN Industrial-Smart** |
|---------|--------------------------------|------------------------|---------------------------|
| **Compressor** | Fixed-speed, on-off cycling | Fixed-speed (no hardware change) | Variable-speed BLDC, modulating |
| **Control** | Mechanical dial thermostat | Monitoring sensors only | Gemini AI + Edge intelligence |
| **Energy Savings** | Baseline | 0-5% (insights only) | **25-40% (hardware efficiency)** |
| **Predictive Maintenance** | None (reactive breakdowns) | Basic alerts | **2-4 week failure prediction** |
| **ROI** | N/A | Unclear value | **18-24 month proven payback** |
| **Refrigerant** | R134a (GWP 1,430) | Unchanged | **R290 (GWP 3)** |

## Common Mistakes to Avoid

❌ **Feature dumping without business value**:
"Has CAN bus communication" → ✅ "CAN bus (ISO 11898) enables seamless integration with existing fleet management systems, eliminating manual data entry"

❌ **Vague claims without quantification**:
"Saves significant energy" → ✅ "37% energy reduction (₹3.1 lakh/year) across 25-location QSR chain"

❌ **Ignoring trade-offs and anti-patterns**:
Only praising product → ✅ Include "Not ideal for [specific scenario]" section

❌ **Overpromising predictions**:
"Predicts all failures" → ✅ "2-4 week failure prediction with 87% confidence for compressor, EEV, and sensor failures"

❌ **Generic competitive positioning**:
"Better than competitors" → ✅ Objective comparison table with specific metrics

## Variables to Customize

When invoking this skill, provide:
- **Product name & model number** (e.g., "ZF-500M Motion-Pro Series")
- **Target ICP** (QSR, cold storage, pharma, mobile, retail)
- **Primary use case** (mobile food truck, stationary QSR, off-grid rural)
- **Competitive context** (vs. traditional, vs. IoT-only, vs. premium international)
- **Price positioning** (entry, standard, premium, luxury tier)

## Output Format

Deliver as:
1. **Markdown document** (primary format for web/editing)
2. **Plain text** (for email/PDF embedding)
3. **HTML** (if requested for web publishing)

Include at the end:
- **Word count**
- **Reading level** (Flesch-Kincaid grade)
- **Key claims to verify** (list any metrics that need customer validation)

---

*This skill is part of the ZAZEN SYSTEMS Co-Writing System*
