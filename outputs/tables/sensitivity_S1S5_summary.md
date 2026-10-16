# Sensitivity analysis of the EMMA recharge apportionment (scenarios S1-S5)

Supplementary analysis of El Farchouni et al., Groundwater for Sustainable Development
(Table SM2, Figure SM14).

## 1. Purpose and rationale

The main workflow (01_EMMA.ipynb) apportions groundwater recharge in the
Haouz-Mejjate aquifer among three end-members, Mountain-Front Recharge (MFR),
regional Mountain-Block Recharge (MBR) and front-slope MBR, using a
three-end-member mass balance with two conservative tracers (δ18O and Cl). The
Monte Carlo error propagation already included in that workflow (N = 1000, each
end-member perturbed randomly within its standard deviation) quantifies the
effect of RANDOM end-member uncertainty. The present sensitivity analysis
complements it by testing the discrete METHODOLOGICAL CHOICES of the workflow.
Each scenario changes exactly one choice while keeping everything else
identical, so any difference in the outcome is attributable to that choice
alone:

- the Na/Cl conservativeness screening of the dataset (S2),
- the choice of isotopic tracer (S3),
- coherent worst-case shifts of all three end-members by +1 and -1 standard
  deviation (S4, S5).

Scenario S1 reproduces the published run exactly and serves as the control: it
proves that the sensitivity notebook implements the same screening, end-member
definitions and mass balance as the main workflow.

## 2. Baseline configuration being tested (published run)

- Dataset: groundwater samples with both δ18O and Cl measurements whose Cl
  passed the conservativeness screening (a sample is flagged reactive only if
  Cl > 100 mg/L AND Na/Cl molar ratio < 0.7), n = 148.
- End-members, defined from the extremes of the full sample pool (all water
  types with both tracers): EM1 (MFR) = mean of the 5 most δ18O-depleted stream
  and spring samples; EM2 (regional MBR) = mean of the 3 highest-Cl groundwater
  samples; EM3 (front-slope MBR) = mean of the 5 most δ18O-enriched samples
  (groundwater, spring, rain) with Cl < 100 mg/L.
- Mixing model: standard three-end-member mass balance (fractions sum to 1, one
  balance equation per tracer), solved analytically per sample. A sample is
  VALID if all three fractions fall within [0, 1], meaning it plots inside the
  mixing triangle.
- Published results: MFR 53.5%, regional MBR 6.4%, front-slope MBR 40.1%, with
  89.2% of samples valid, and Monte Carlo mean standard errors of 5.2%, 0.7%
  and 5.3% respectively.

## 3. Scenario definitions

| Scenario | What changes vs S1 | What it tests |
|---|---|---|
| S1 | Nothing (exact reproduction of the published run) | Control, implementation check |
| S2 | The reactive-flagged groundwater samples are re-included | Influence of the Na/Cl screening decision |
| S3 | Tracer pair δ2H + Cl instead of δ18O + Cl; end-member δ2H values are the measured means of the same defining samples | Independence from the choice of isotopic tracer |
| S4 | All three end-members shifted by +1 SD in both tracers simultaneously | Coherent worst-case end-member bias (upper direction) |
| S5 | All three end-members shifted by -1 SD in both tracers simultaneously (Cl floored at 0) | Coherent worst-case end-member bias (lower direction) |

S4 and S5 are deliberately harsher than the Monte Carlo perturbation: they move
all three end-members in the same direction at once, a configuration that
random sampling almost never produces.

## 4. End-member compositions (mean ± SD of the defining samples)

| End-member | δ18O (‰ VSMOW) | δ2H (‰ VSMOW, measured) | Cl (mg/L) | n |
|---|---|---|---|---|
| EM1 (MFR) | -9.07 ± 0.27 | -57.5 ± 2.8 | 6.3 ± 2.9 | 5 |
| EM2 (Regional MBR) | -4.87 ± 0.82 | -33.9 ± 6.4 | 1969.0 ± 180.5 | 3 |
| EM3 (Front-slope MBR) | -4.70 ± 0.29 | -25.3 ± 4.6 | 11.6 ± 10.4 | 5 |

The δ2H values used in S3 are the measured means of the same samples that
define each end-member (not derived from the local meteoric water line).

## 5. Results

| Scenario | n | Valid % | MFR % | Regional MBR % | Front-slope MBR % |
|---|---|---|---|---|---|
| S1 | 148 | 89.2 | 53.5 | 6.4 | 40.1 |
| S2 | 158 | 89.2 | 53.8 | 6.7 | 39.5 |
| S3 | 148 | 87.8 | 58.4 | 6.3 | 35.4 |
| S4 | 148 | 80.4 | 60.9 | 5.5 | 33.7 |
| S5 | 148 | 93.2 | 48.1 | 7.0 | 44.8 |

Deviations from baseline S1 (percentage points):

| Scenario | ΔMFR | ΔRegional MBR | ΔFront-slope MBR |
|---|---|---|---|
| S2 | +0.3 | +0.3 | -0.6 |
| S3 | +4.9 | -0.1 | -4.7 |
| S4 | +7.4 | -0.9 | -6.4 |
| S5 | -5.4 | +0.6 | +4.7 |

Maximum absolute deviations across S2-S5: MFR 7.4
points, regional MBR 0.9 points, front-slope MBR
6.4 points.

## 6. Interpretation

1. The source ordering (MFR > front-slope MBR > regional MBR) is preserved in
   all five scenarios. MFR remains the dominant recharge source in every
   configuration, ranging from 48.1% to 60.9% around the
   baseline 53.5%.
2. S2: re-including the reactive samples changes the fractions by at most
   0.6 points, showing that the screening decision does not drive the
   results.
3. S3: the independent tracer pair δ2H + Cl reproduces the same apportionment
   within 4.9 points on MFR; the shift trades
   almost entirely between MFR and front-slope MBR because these two
   end-members are separated mainly along the isotopic axis, while regional MBR
   is essentially unchanged.
4. S4 and S5: even coherent 1 SD shifts of all three end-members keep MFR
   between 48.1% and 60.9%, a bracket consistent with
   the Monte Carlo standard errors. The validity rate responds as the triangle
   geometry predicts (triangle shrinks in S4, valid 80.4%;
   expands in S5, valid 93.2%).
5. The regional MBR estimate is the most stable (5.5 to
   7.0%) because the very high Cl of EM2 makes it chemically
   distinctive; this also explains its small Monte Carlo standard error (0.7%).

Conclusion: the recharge apportionment is robust to the tested methodological
choices. The dominant role of MFR (about half of the recharge) is not an
artefact of the screening, the tracer selection, or the exact end-member
coordinates.

## 7. Files and reproducibility

Produced by notebooks/05_EMMA/02_EMMA_sensitivity.ipynb, which reads
outputs/intermediate/data_EMMA1.xlsx and data/All_data1.xlsx and writes:

- outputs/tables/sensitivity_S1S5_results.csv (scenario table, Table SM2)
- outputs/tables/sensitivity_S1S5_summary.md (this document)
- outputs/figures/SM14_EMMA_sensitivity_S1S5.png (grouped bar figure)

Scenario S1 is checked automatically against the published values at run
time.
