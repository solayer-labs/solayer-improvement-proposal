# SIP-1: Setting InfiniSVM PoS Inflation Schedule

## Overview

InfiniSVM’s execution layer relies on a central sequencer (paid in SOL) plus a lightweight mesh of checker / verifier nodes who attest to state validity. Solayer wants to bootstrap and provide adequate rewards to incentivize validators to continue to provide security to our blockchain.

This proposal formalises the inflation schedule for InfiniSVM’s LAYER token. A high‑reward launch phase (**8% inflation**) is followed by a programmed **15% year‑over‑year reduction** until the rate locks at **2%**. Rewards are paid every epoch so that total issuance over 365 days equals the headline annual percentage. The design supplies attractive early yields, tapers predictably as network revenues grow, and settles at a level widely regarded as “sound‑money” inflation.

Our goal is therefore to:

- **Bootstrap security fast** with headline rewards that cover hardware + risk premium.  
- **Fade subsidy** to “sound‑money” levels once the network and fee rails mature.

By approving this proposal, the Solayer community will implement an inflation schedule for the InfiniSVM chain’s LAYER token. An initial **8% → 2% decreasing inflation curve** is designed to maximize early network security and participation while ensuring the LAYER token remains sound and scarce in the long term. This approach takes into account what has worked for prominent Layer-1s and Layer-2s that we have extensively researched, and adapts it to our unique context as an SVM L1 chain with a mega leader architecture.

### Benefits for Stakeholders

- **Verifier Node Operators (Stakers):**  
  Can be confident their efforts will be rewarded with high APR in the beginning, and that the value of rewards is protected as the inflation schedule tapers off. They can plan their operations knowing the reward schedule in advance.

- **LAYER Token Holders:**  
  Can be assured that inflation will not be uncontrolled, as it will be front-loaded for network growth and then limited to 2% annually. This encourages staking and participation, while ensuring long-term dilution is minimal and predictable.

- **Ecosystem Developers & Partners:**  
  Gain a network that is secure due to strong staking incentives without fear of hyperinflation. A robust validator set improves reliability and decentralization, attracting more usage and integrations to InfiniSVM.

---

## Specification

The inflation schedule is parameterised on‑chain; governance may modify the initial rate, decay factor, or floor via a simple parameter vote if staking participation, fee flows, or market conditions diverge from projections.

### Proposed Parameters

- **Initial inflation:** 8 % of total supply per year  
- **Annual disinflation:** inflation × 0.85 each year (‑15 %)  
- **Steady‑state floor:** 2 % per year once reached  
- **Distribution cadence:** minted each epoch; finalized every 1 full calendar-year  
- **Allocation:** 100% of newly minted LAYER to validators and delegates based on inflation schedule  

### Inflation Schedule

![Inflation Schedule](/governance/images/sip_1_inflation_schedule.png)

| Year   | Rate   |
|--------|--------|
| 1      | 8.00% (start) |
| 2      | 6.80% |
| 3      | 5.78% |
| 4      | 4.91% |
| 5      | 4.17% |
| 6      | 3.55% |
| 7      | 3.02% |
| 8      | 2.57% |
| 9      | 2.19% |
| 10+    | 2.00% (fixed) |

---

## Reward Calculation

At the start of each epoch, the protocol computes:

```

epoch_inflation = annual_rate / epochs_per_year

```

and mints that share of supply to the staking module. Because epochs carry a fixed slot count, variations in block time do not distort headline inflation, preventing timing arbitrage.

### Distribution Mechanics

- All minted LAYER flows to validators and their delegators, proportional to stake, with optional commission splits set by each validator.  
- The sequencer continues to earn external SOL fees; it receives no share of inflation, eliminating dual‑reward conflicts.

---

## Voting

You may vote for the following:

- **YES** — adopt the 8 % → 2 % disinflation curve and activate PoS rewards immediately.  
- **NO** — retain zero rewards for verifiers (status‑quo).  
- **ABSTAIN** — use if you believe more discussion is required.

### Success Threshold

This proposal will pass if **70% of community votes** are cast as YES.  
For more information on Solayer's governance and voting parameters:  
[Solayer Realms DAO](https://app.realms.today/dao/AYgtQCZGaYZywkAT7fWDGWeL3hzaXCgB72WcWaNgpgbt)

