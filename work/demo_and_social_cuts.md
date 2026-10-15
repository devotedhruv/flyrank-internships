# ML-12: Tell the Story — Showcase Demo Outline & Shareable Cuts

**Author:** Dhurbaraj Singh  
**Track:** Machine Learning (`ML`) · Week 8 · Phase: Submit  
**Project:** FlyRank Search Intelligence Capstone (Lane 2: Refresh / Content Opportunity Scoring)  
**Deployed Research Paper:** [https://devotedhruv.github.io/flyrank-internships/](https://devotedhruv.github.io/flyrank-internships/)  
**GitHub Repository:** [https://github.com/devotedhruv/flyrank-internships](https://github.com/devotedhruv/flyrank-internships)  

---

## 1. 5-Minute Showcase Demo Outline

*Designed for the Week 8 Capstone Showcase (5 minutes total).*

### [0:00 – 1:00] The Question & The Problem
- **The Core Question:** Which published content items across an enterprise catalog are at the highest risk of organic search visibility decay, and how can editorial teams prioritize their limited refresh capacity?
- **The Enterprise Reality:** Editorial and SEO teams typically have the capacity to rewrite or refresh only 20–50 URLs per sprint. Without machine learning, teams rely on crude heuristics or gut feel—either wasting days rewriting healthy cornerstone pages with seasonal dips, or noticing decay only after articles collapse off Google Page 1.

### [1:00 – 2:00] The Data & Leakage-Free Methodology
- **The Dataset:** 30,000 URLs across 32 pseudonymous enterprise client domains over a 90-day observation window from FlyRank's telemetry.
- **Zero Leakage:** Strictly quarantined 8 outcome-window metrics (e.g., `trend_pct`, 30-day post-window impressions and sessions).
- **Grouped Validation:** Evaluated under a grouped client-holdout split (28 training domains vs. 4 completely unseen test domains), preventing domain-level memorization.
- **Features:** 52 signals spanning historical demand, index presence consistency, rank trajectory, content age, word counts, and search intent tiers.

### [2:00 – 3:00] The Chart: Figure 1 (Feature Importance)
- **One Visual:** Display `Figure 1: Top Feature Importances (Random Forest)`.
- **The Finding:** Index appearance frequency (`days_with_impressions` at 16.06%) is the single strongest predictor of stability vs. algorithmic erosion. When an article drops from 90 days of continuous impressions to sporadic weekly appearances, it signals decay long before traffic crashes.
- **Moat Effect:** Content depth (`word_count` + `char_count`) forms a defensive moat; pages under 600 words decay 2.4× faster under query competition.

### [3:00 – 4:00] The Honest Result: Model vs. Heuristic Baseline
- **The Baseline:** Standard SEO weighted heuristic (`0.40*Rank(Impr) + 0.30*Rank(Age) + 0.25*Rank(1/Pos)`).
- **The Result on Unseen Clients:**
  - Heuristic Baseline: **Precision@50 = 0.240** (worse than random guessing due to selecting stable evergreen head terms).
  - Random Forest Ensemble: **Precision@50 = 0.700** (a **2.92× lift**), **ROC AUC = 0.747**.
- **Honest Framing:** This is an observational decision-support model, not a causal proof of Google ranking mechanics. Causal validation requires prospective A/B testing.

### [4:00 – 5:00] The Recommendation & Action Playbook
- **Operational Output:** Translates raw probabilities into a reason-coded triage queue across 30,000 URLs:
  - **43.6% (`monitor`):** Stable assets—leave alone, saving 100+ wasted hours.
  - **22.2% (`refresh_and_review_ctr`):** Strong page-one ranking, low CTR → title/meta description rewrite.
  - **27.3% (`refresh`):** Core body refresh and internal link reinforcement.
  - **6.6% (`refresh_and_review_engagement`):** UX, intro restructuring, and table of contents.
  - **0.3% (`expand_and_refresh`):** Thin articles under 500 words.
- **Immediate Sprint Impact:** In a 50-URL editorial sprint, the top-ranked cohort delivers ~35 verified high-impact opportunities versus ~12 from heuristic sorting.

---

## 2. Shareable Cut 1: Methodology Social Post (LinkedIn / X)

> **Can machine learning predict which published content is decaying in Google Search before traffic falls off a cliff?**
>
> In my FlyRank Search Intelligence Capstone, I trained and validated a predictive refresh opportunity model on 30,000 URLs across 32 enterprise client domains.
>
> 🔍 **Methodology & Leakage Defense:**
> Standard random train/test splits severely leak domain authority across splits. I implemented a grouped client-holdout split (evaluating only on unseen client domains) and quarantined 8 outcome-window metrics to guarantee zero look-ahead bias across 52 behavioral signals.
>
> 📊 **What the Data Showed:**
> • Precision@50 jumped from 24% (heuristic SEO baseline) to 70% (Random Forest)—a **2.92× lift** in finding high-value refresh candidates.
> • The #1 predictor of decay isn't keyword volume or rank position—it's **index presence consistency** (`days_with_impressions`). When continuous appearance drops to sporadic weekly impressions, algorithmic erosion has already started.
> • High search volume queries decay at virtually the same rate as long-tail queries (<1.1% importance).
>
> 🚀 **The Output:**
> An automated, reason-coded editorial playbook triaging 43% of catalog inventory to passive monitoring, focusing limited writing hours where revenue impact is highest.
>
> 📄 Read the full deployed research paper: https://devotedhruv.github.io/flyrank-internships/  
> 💻 Reproducible Code & Artifacts: https://github.com/devotedhruv/flyrank-internships  
>
> *Built on the FlyRank ML Internship dataset (https://flyrank.ai).*
>
> #MachineLearning #DataScience #SEO #SearchIntelligence #RandomForest #ReproducibleAI

---

## 3. Shareable Cut 2: 3-Sentence Employer-Facing Summary

> "I engineered an end-to-end Machine Learning search intelligence pipeline on 30,000 multi-client enterprise search records from FlyRank's telemetry that predicts organic visibility decay using 52 behavioral and technical signals. Evaluated under a grouped client-holdout cross-validation split with strict leakage quarantines, my Random Forest model achieved an ROC AUC of 0.747 and boosted top-50 recommendation precision from 24% to 70% (a 2.92× lift) over standard industry heuristics. I translated these predictions into an operational, reason-coded editorial action playbook deployed as an open-access research paper and reproducible GitHub repository."

---

## 4. Verification & Submission Checklist
- [x] Paper abstract & introduction tie findings to real FlyRank content problem.
- [x] 5-minute demo outline covers Question, Method, One Chart, One Honest Result, One Recommendation.
- [x] Social post methodology cut crafted with honest claim language and live links.
- [x] 3-sentence employer summary captures what was built, on what data, and what it showed.
- [x] Committed to `work/demo_and_social_cuts.md` and included in `work/notebooks/capstone.ipynb` and `work/notebooks/w07_action_playbook.ipynb`.
