# Blue Sky Mommy Shield
## Postpartum Depression Insurance: Product Design and Actuarial Pricing Research

**Project type:** Collaborative academic insurance product research  
**Competition:** Entry to the 15th China Risk Management and Actuarial Forum (第十五届中国风险管理与精算论坛)  
**Focus:** Health insurance · Product design · Actuarial pricing · Risk analysis

## Overview

Blue Sky Mommy Shield is a proposed group supplemental medical insurance product designed to address financial risks associated with postpartum depression in China. The project examines market needs, insurability, product design, pricing methodology, and risk management. It is an **academic proposal**, not an insurance product available for sale.

The proposed coverage includes eligible outpatient and inpatient treatment costs, together with supporting services such as psychological counseling and medical consultation.

## Research approach

### 1. Market needs assessment
The team investigated awareness of postpartum depression, customer preferences, and willingness to purchase insurance. In the questionnaire results presented in the Chinese project report, **67% of respondents said they would consider purchasing** this type of insurance. This measures stated interest, not actual purchase behavior.

### 2. Insurance product design
The project proposed an employer-sponsored group supplemental medical insurance structure, with defined eligibility criteria, coverage provisions, deductibles, reimbursement terms, claims procedures, and supplementary support services.

### 3. Actuarial pricing framework
The report outlines an **experience-frequency-based** approach to estimating expected covered medical expenses per insured person. The proposed methodology considers:

- Medical expenses subject to a deductible and coverage limit;
- The number of insured individuals in the base period;
- The contractual reimbursement percentage; and
- Adjustments such as medical-cost growth.

The report also discusses geographic and individual-level factors that may influence risk and expected medical costs. The original work presents a pricing *framework*; this repository does not claim that a production-ready premium model or validated final market rate was developed.

### 4. Risk management
The research evaluates insurability, potential adverse selection, moral hazard, product sustainability, and the role of group coverage and contractual limits in managing insurance risk.

## My contributions

As a member of the project team, I contributed to questionnaire design, market-demand analysis, the review of incidence and medical-cost sources, and research supporting actuarial pricing assumptions. This repository presents the collaborative project's findings while distinguishing my individual contributions.

## Technical extension (implemented)

The notebook [`experience_frequency_pricing.ipynb`](experience_frequency_pricing.ipynb) reproduces the report's pricing formula in Python using **synthetic data**:

- Implements the literal bounded-range form of the experience-frequency formula, with input validation;
- Checks the arithmetic against a small hand-calculated example;
- Runs a sensitivity analysis on reimbursement rate (α) and medical-cost trend (γ), with a chart; and
- Compares the literal formula with an alternative "capped expense basis" reading of the upper limit.

With the illustrative assumptions (10,000 insured, 10% event rate, CNY 1,500 deductible, CNY 25,000 limit, 80% reimbursement, 5% trend), the adjusted expected covered cost is about **CNY 703 per insured per year** (about CNY 779 under the alternative reading). These figures come from invented inputs and are **not** premium estimates.

Formula definitions, assumptions and open interpretation questions are documented in [`PRICING_METHODOLOGY.md`](PRICING_METHODOLOGY.md).

**Still to do:** calibrate claim frequency and costs with appropriately licensed public data, and add sensitivity on claim frequency.

## Repository structure

| File | Contents |
| --- | --- |
| `README.md` | Project overview |
| `PRICING_METHODOLOGY.md` | Pricing formula, parameter definitions, assumptions and limitations |
| `experience_frequency_pricing.ipynb` | Python implementation with synthetic data and sensitivity analysis |
| `Original_Chinese_Report.pdf` | Original collaborative report (Chinese) |
| `requirements.txt` | Python dependencies |

## How to run

```bash
pip install -r requirements.txt
jupyter notebook experience_frequency_pricing.ipynb
```

The random seed is fixed (`2024`), so results are reproducible.

## Source report and attribution

Original research title: **“蓝天妈咪护盾”——产后抑郁症保险**  
English working title: **Blue Sky Mommy Shield — Postpartum Depression Insurance**

The underlying report was submitted to the **15th China Risk Management and Actuarial Forum (第十五届中国风险管理与精算论坛)** and was jointly prepared by **Xu Ziru, Chen Yang, and Yu Jiahui**, with academic supervision. The original report is written in Chinese and is included here as [`Original_Chinese_Report.pdf`](Original_Chinese_Report.pdf) with the team's permission. Underlying survey responses are not published.

## Limitations and disclaimer

The results reflect the sources and assumptions used in the original research period, not current insurance-market or medical-cost estimates. The work is educational and should not be interpreted as medical advice, an insurance quotation, or an approved insurance policy. No individual-level health or survey responses are shared here.
