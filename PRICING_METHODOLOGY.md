# Experience-Frequency Pricing Methodology

## Source
This portfolio extension is based on **Chapter 5, Product Pricing Research (产品定价研究)**, specifically **Section (II), Pricing Method (定价方法)**, PDF page 24 (printed page 19), of the collaborative report *“蓝天妈咪护盾”——产后抑郁症保险*.

## Original equation

\[
P(x) = \frac{C(M_1,M_2)-N(M_1,M_2)\times M_1}{N'}\times\alpha\times\gamma
\]

| Original symbol | Meaning in the report |
| --- | --- |
| \(M_1\) | Deductible / starting threshold |
| \(M_2\) | Upper payment limit |
| \(C(M_1,M_2)\) | Total claim amount for relevant risk events |
| \(N(M_1,M_2)\) | Number of insured individuals above the deductible and below the upper limit |
| \(N'\) | Baseline-period insured population |
| \(\alpha\) | Contractual payout / reimbursement proportion |
| \(\gamma\) | Medical-cost growth and related adjustment factor |

The equation estimates an adjusted **expected covered claim cost per baseline insured person** under a simplified methodology. It is not, by itself, a fully loaded commercial premium.

## Notebook implementation

The notebook's first function follows the *literal bounded-range interpretation*: aggregate eligible annual amounts where \(M_1 < \text{annual cost} < M_2\), subtract \(M_1\) per eligible individual, divide by \(N'\), then multiply by \(\alpha\gamma\).

**Important ambiguity:** The original report describes \(M_2\) as an upper *payment* limit, but its displayed formula and description do not unambiguously specify how above-limit claims are paid. A real policy may handle these claims with a limit on eligible cost or on the benefit paid. The notebook compares one alternative interpretation separately, without presenting it as a fact from the source.

## Inputs and evidence

- **Source-supported:** formula; named parameters; the need to reflect deductibles, upper limits, reimbursement rate, baseline population and trend.
- **Illustrative only:** 10,000 insured, 10% assumed event rate, synthetic gamma-distributed medical costs, CNY 1,500 deductible, CNY 25,000 upper limit, 80% reimbursement, 5% trend.
- **Unavailable:** claimant-level medical expenses, historical insured exposures, empirically calibrated rate factors and confirmed complete benefit schedule.

The questionnaire willingness-to-purchase figure is *demand information*, not a claim frequency. Published rates from different cohorts should not be combined without reviewing exposure definitions and comparability.

## Attribution and confidentiality

The original research was co-authored by Xu Ziru, Chen Yang, and Yu Jiahui. No original participant-level health records or employer/insurer confidential records are used in this demonstration.
