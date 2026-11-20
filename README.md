<div align="center">
  <h2>Rooftop Solar PV for a Karachi Household: Net Metering vs Net Billing</h2>
  <p><b>Complex Engineering Problem (CEP)</b></p>
</div>

> **Course:** ME-424 · Clean Energy Technology  
> **University:** NED University of Engineering & Technology, Karachi  
> **Tools:** PVGIS24 (European Commission JRC) · Excel (Techno-economic Model)  
> **Submitted to:** Dr Abdual Ghafar

---

## Table of Contents

1. [Overview](#overview)
2. [Key Results](#key-results)
3. [Tools and Technologies](#tools-and-technologies)
4. [Household and Site Data](#household-and-site-data)
5. [Solar Resource and System Design](#solar-resource-and-system-design)
6. [Regulatory and Tariff Framework](#regulatory-and-tariff-framework)
7. [Methodology](#methodology)
8. [Results in Detail](#results-in-detail)
9. [Sensitivity Analysis](#sensitivity-analysis)
10. [Mitigation Strategy and Recommendation](#mitigation-strategy-and-recommendation)
11. [Assumptions and Limitations](#assumptions-and-limitations)
12. [Future Work](#future-work)
13. [Repository Structure](#repository-structure)
14. [How to Reproduce](#how-to-reproduce)
15. [References](#references)
16. [License](#license)
17. [Author](#author)
18. [Acknowledgments](#acknowledgments)

---

## Overview

In February 2026, NEPRA's (Prosumer) Regulations, 2026 (**SRO 251(I)/2026**, notified 9 February 2026) replaced unit-for-unit **net metering** with **net billing**. Under net billing, imported electricity is billed at the applicable tariff, while exported electricity is credited only at the National Average Energy Purchase Price (NAEPP, about Rs 11/kWh).

This project takes **one real K-Electric household** in Liaqatabad, Karachi, and:

- designs a **battery-less, grid-tied rooftop PV system** from the household's actual consumption,
- evaluates the **same system and the same load** under both regimes,
- quantifies the **extra annual cost** caused by net billing,
- calculates the **payback period** under each regime, and
- proposes a **practical mitigation strategy**.

---

## Key Results

| Metric | Value |
|---|---|
| Selected system | **1.0 kWp**, grid-tied inverter, no battery |
| Annual generation (PVGIS) | 1,927 kWh (1,926.85 kWh/kWp) |
| Self-consumed on site | 857.5 kWh (44.5 %) |
| Exported to grid | 1,069.3 kWh (55.5 %) |
| Annual bill without PV | Rs 73,813 |
| Annual bill, net metering | Rs 9,521 |
| Annual bill, net billing | Rs 29,595 (**60 % lower than no PV**) |
| **Extra cost of net billing** | **Rs 20,074 / year** (31 % of the net-metering saving lost) |
| Simple payback, net metering | 2.0 years |
| Simple payback, net billing | 2.9 years |
| Payback with 0.5 %/yr degradation and 1 %/yr O&M | 3.0 years (net billing) |
| Annual bill with mitigation (3 % load shift) | Rs 27,798 |

**Conclusion:** Net billing reduces the benefit of rooftop solar, but a correctly sized system still pays back in about 3 years, well inside the five-year agreement term. The retail tariff it displaces (about Rs 32 to 44/kWh with taxes) is far higher than the export price.

---

## Tools and Technologies

| Tool | Purpose |
|---|---|
| **PVGIS24** (European Commission JRC, ERA5 database) | Solar resource and monthly PV yield per kWp |
| **Microsoft Excel** | Monthly techno-economic model: tariff function, net metering and net billing logic, payback, sensitivity |
| **K-Electric bills (May to Oct 2026)** | Consumption data and validation of the tariff model |
| **NEPRA SRO 251(I)/2026 and SRO 279(I)/2026** | Regulatory framework and A1-R tariff slabs |

---

## Household and Site Data

| Item | Value |
|---|---|
| Utility | K-Electric (Liaqatabad Customer Care Centre) |
| Location | Liaqatabad, Karachi, Pakistan (24.914° N, 67.050° E) |
| Tariff category | A1-R (residential) |
| Sanctioned / connected load | 1 kW / 1 kW |
| Meter | Single-phase electronic meter |
| Building | Flat in an apartment building with a flat concrete roof |

### Consumption profile

Monthly units come from the 13-month usage history on the October 2026 K-Electric bill and the six bills for May to October 2026. Only the "Electricity Charges for current month" are used; arrears, installments and late-payment surcharges are excluded.

| Statistic | Value |
|---|---|
| Annual consumption | 2,077 kWh |
| Average | 173 kWh/month (5.69 kWh/day) |
| Peak month | July (254 kWh) |
| Lowest month | February (73 kWh) |
| Winter average (Nov to Apr) | 117 kWh/month |
| Summer average (May to Oct) | 230 kWh/month |

Consumption is strongly seasonal: summer demand is almost twice winter demand.

### Load timing (daytime vs evening)

An appliance survey gives a daytime load of 2.54 kWh/day and an evening/night load of 3.61 kWh/day. The surveyed total (6.14 kWh/day) is within a ratio of 1.08 of the billed average (5.69 kWh/day).

- **Daytime fraction (8 am to 5 pm): 41.3 %**
- **Evening and night fraction: about 59 %**

This fraction splits every month's consumption into PV-usable daytime load and evening load.

---

## Solar Resource and System Design

### PVGIS simulation

| Input | Value |
|---|---|
| Database | PVGIS-ERA5 (PVGIS24, European Commission JRC) |
| Location | 24.914° N, 67.050° E |
| Technology | Crystalline silicon |
| Installed power | 1.00 kWp (to obtain yield per kWp) |
| Mounting | Triangle mounting on flat roof |
| Slope / azimuth | 29° (PVGIS-optimised) / 0° (south) |
| Losses | Cable 1 %, inverter 2 %, PV 0.5 %; total system losses 14.77 % |

**Annual specific yield: 1,926.85 kWh/kWp.** June to September output is lower because of monsoon cloud, while demand is highest in these months. This is a generation-demand mismatch.

### Sizing constraints

1. **Regulatory limit.** Regulation 3(2) of SRO 251(I)/2026 caps DG capacity at the sanctioned load, so the maximum is **1 kWp**.
2. **Self-consumption limit.** Without a battery, only the daytime load (about 857 kWh/year) can use PV directly. One kWp already generates 1,927 kWh, so anything larger is exported at the low NAEPP rate.

| PV size (kWp) | Generation (kWh/yr) | Self-consumed (kWh/yr) | Exported (kWh/yr) | Export share | Net-billing payback (yr) | Marginal payback (yr) |
|---|---|---|---|---|---|---|
| 0.50 | 963 | 722 | 241 | 25 % | 2.2 | n/a |
| 0.75 | 1,445 | 841 | 604 | 42 % | 2.5 | 3.8 |
| **1.00** | **1,927** | **858** | **1,069** | **55 %** | **2.9** | **5.7** |
| 1.50 *(hypothetical)* | 2,890 | 858 | 2,033 | 70 % | 3.6 | 6.1 |

### Selected system

**1.0 kWp** (for example, two 500 Wp modules) with a grid-tied inverter and no battery. Required roof area is about 6 m² (assumed 6 m²/kWp, not measured on site).

---

## Regulatory and Tariff Framework

### Net metering vs net billing

| Aspect | Net metering (2015, closed to new applicants since 9 Feb 2026) | Net billing (SRO 251(I)/2026) |
|---|---|---|
| Exchange | Unit-for-unit; surplus carried forward | Imports and exports priced separately (Reg 14(1)) |
| Imports | Net units billed at tariff | All imported kWh billed at the applicable tariff |
| Exports | Netted against imports; surplus about Rs 25.9 to 27/unit | Credited at NAEPP, about Rs 10 to 11/unit (Reg 14(1)(b)) |
| Negative bill | n/a | Credited to next cycle or paid quarterly (Reg 14(2)) |
| Term | Seven years | Five years, renewable (Reg 7) |
| Rate revision | Fixed in agreement | NEPRA may revise during the agreement (Reg 14(3)) |
| Capacity limit | Sanctioned load | Not above sanctioned load (Reg 3(2)) |

Because new connections fall only under net billing, net metering is used here as the **counterfactual**: the same PV system and load evaluated under the earlier framework.

### Tariff used (K-Electric A1-R, SRO 279(I)/2026)

| Monthly units | Unprotected rate (Rs/kWh) | Fixed charge (Rs/month) |
|---|---|---|
| 1 to 100 | 22.44 | 275 |
| 101 to 200 | 28.91 | 300 |
| 201 to 300 | 33.10 | 350 |
| 301 to 400 | 36.46 | 400 |

Additional bill components: financing-cost (PHL) surcharge Rs 3.23/kWh, electricity duty 1.5 %, sales tax 18 %, and MUCT Rs 40. The household was a protected consumer until April 2026, so November to April are billed on protected slabs and May to October on unprotected slabs, as observed on the bills.

---

## Methodology

All calculations are done in an Excel model at **monthly resolution**. For month *m* with load *L*, PV size *P*, specific yield *y*, generation *G = P × y*, and daytime load *D = 0.413 × L*:

```text
Self-consumed   S = min(G, D)
Export          X = G - S
Grid import     I = L - S
```

**Tariff function:**

```text
E       = F + u (r + 3.23)
Bill(u) = E + 0.015 (E - F) + 0.18 [E + 0.015 (E - F)] + 40
```

where *u* is billed units, *r* the slab rate, and *F* the fixed charge.

| Scenario | Bill calculation |
|---|---|
| No PV (baseline) | `Bill(L)` |
| Net metering | `Bill(max(0, I - X - credit brought forward))`, surplus carried forward |
| Net billing | `Bill(I) - X × 11` |

### Model validation

The tariff model was checked against nine actual bills (Feb to Oct 2026). It reproduces eight of nine months within 5 % and the nine-month total within **0.4 %** (Rs 69,253 modelled vs Rs 69,506 actual). The October 2026 bill (238 units) was also reconstructed by hand to the paisa (Rs 11,314.19). Remaining differences come from monthly fuel and quarterly adjustments (FCA, QTA), which are not modelled.

---

## Results in Detail

### Monthly results for the 1.0 kWp system (Rs)

| Month | Load (kWh) | PV (kWh) | Export (kWh) | Import (kWh) | No PV | Net metering | Net billing | Net billing + load shift |
|---|---|---|---|---|---|---|---|---|
| Nov | 114 | 169.6 | 122.5 | 66.9 | 2,232 | 453 | -272 | -267 |
| Dec | 75 | 176.7 | 145.7 | 44.0 | 1,150 | 453 | -740 | -737 |
| Jan | 78 | 180.5 | 148.3 | 45.8 | 1,178 | 453 | -753 | -749 |
| Feb | 73 | 170.4 | 140.2 | 42.9 | 1,131 | 453 | -691 | -688 |
| Mar | 181 | 185.8 | 111.1 | 106.3 | 3,278 | 453 | 890 | 865 |
| Apr | 179 | 176.9 | 103.1 | 105.1 | 3,246 | 453 | 960 | 305 |
| May | 218 | 170.2 | 80.2 | 128.0 | 9,939 | 365 | 4,439 | 4,259 |
| Jun | 253 | 140.8 | 36.4 | 148.5 | 11,462 | 365 | 5,712 | 5,503 |
| Jul | 254 | 120.8 | 15.9 | 149.1 | 11,505 | 365 | 5,960 | 5,750 |
| Aug | 219 | 117.9 | 27.4 | 128.6 | 9,982 | 1,426 | 5,042 | 4,861 |
| Sep | 195 | 143.8 | 63.3 | 114.5 | 7,900 | 1,939 | 4,105 | 3,944 |
| Oct | 238 | 173.6 | 75.3 | 139.7 | 10,809 | 2,346 | 4,945 | 4,748 |
| **Year** | **2,077** | **1,926.8** | **1,069.3** | **1,219.5** | **73,813** | **9,521** | **29,595** | **27,798** |

Negative net-billing values in winter are credits carried to the next billing cycle (Reg 14(2)).

### Annual comparison and payback

| | No PV | Net metering | Net billing | Net billing + load shift |
|---|---|---|---|---|
| Annual bill (Rs) | 73,813 | 9,521 | 29,595 | 27,798 |
| Annual saving vs no PV (Rs) | n/a | 64,291 | 44,218 | 46,015 |
| Extra cost vs net metering (Rs/yr) | n/a | 0 | 20,074 | 18,276 |
| Share of net-metering saving lost | n/a | 0 % | 31 % | 28 % |
| Capital cost (Rs) | n/a | 130,000 | 130,000 | 130,000 |
| Simple payback (years) | n/a | 2.0 | 2.9 | 2.8 |
| Payback with degradation and O&M (years) | n/a | 2.1 | 3.0 | 2.9 |

Capital cost is a market estimate of **Rs 130,000/kWp** (Rs 120,000 to 140,000/kW, SolarApp.pk, 2026). Tariff escalation is taken as 0 % (conservative).

---

## Sensitivity Analysis

**Export (buyback) rate**

| Buyback rate (Rs/kWh) | Annual net-billing bill (Rs) | Extra cost vs net metering (Rs/yr) | Simple payback (yr) |
|---|---|---|---|
| 8.13 | 32,664 | 23,143 | 3.2 |
| 10 | 30,665 | 21,143 | 3.0 |
| **11** | **29,595** | **20,074** | **2.9** |
| 13 | 27,457 | 17,935 | 2.8 |

**Installed cost**

| Installed cost (Rs/kWp) | 100,000 | 130,000 | 160,000 |
|---|---|---|---|
| Net-billing simple payback (yr) | 2.3 | 2.9 | 3.6 |

In every case the net-billing payback stays below the five-year agreement term.

---

## Mitigation Strategy and Recommendation

**Strategy: right-size the system and shift flexible evening load into daytime.**

1. **Right-sizing.** Exports earn only Rs 11/kWh against Rs 32 to 44/kWh for avoided imports, so capacity beyond the daytime load has a marginal payback of 5.7 to 6.1 years. The system is capped at 1.0 kWp, which is also the regulatory maximum for a 1 kW sanctioned load.
2. **Load shifting.** Without a battery, self-consumption can only rise by moving discretionary loads into 8 am to 5 pm (for example, the evening microwave use, water pump and charging loads). A 3 % shift reduces the annual net-billing bill from Rs 29,595 to Rs 27,798, saving about **Rs 1,800/year**.
3. **Slab management.** Keep monthly imports below 100 and 200 unit boundaries to benefit from cheaper slabs and, if imports stay at or below 200 units for six months, protected-consumer status.

**Recommendation:** Install a 1.0 kWp battery-less grid-tied system. The annual bill falls from about Rs 73,800 to Rs 29,600 (a 60 % reduction), net billing costs Rs 20,074/year more than the old regime, and the investment still pays back in about 3 years. Do not install more than 1 kWp unless the sanctioned load is raised and a battery or large daytime load is added. A battery is excluded by the problem statement but is the logical next step as costs fall.

---

## Assumptions and Limitations

- **Monthly, not hourly, energy balance.** `min(PV, daytime load)` is optimistic compared with an hourly simulation.
- **Estimated bills.** November 2025 to January 2026 bills are model estimates (about ±Rs 300/month); protected-slab rates were calibrated to Feb to Apr bills; FCA/QTA adjustments are not modelled.
- **Repeating pattern.** The protected/unprotected pattern of the last twelve months is assumed to repeat.
- **Typical-year yield.** PVGIS year-to-year variability is about 1.3 %; dust and shading are not separately modelled.
- **NAEPP risk.** The Rs 11 export rate may be revised by NEPRA during the agreement (Reg 14(3)); Rs 8.13 and Rs 13 are shown as sensitivities.
- **Costs.** Capital cost is a market estimate, not a vendor quotation. Interconnection and metering costs (Reg 12), including any upgrade from a single-phase connection, are excluded.
- **Eligibility.** The regulations define the applicant as a three-phase consumer; eligibility of the existing single-phase connection must be confirmed with K-Electric.
- **Roof.** Roof area and permission to use the shared roof of the apartment building were not verified.
- **Economics.** No inflation, tariff escalation or discounting; 0.5 %/yr degradation and 1 %/yr O&M are assumed. Net-metering surplus credits are not monetised at year end.

---

## Future Work

- Replace the monthly energy balance with an **hourly simulation** using measured or typical hourly load profiles.
- Add a **battery storage case** and find the battery cost at which storage pays back under net billing.
- Obtain **vendor quotations** and include interconnection and meter-upgrade costs (Reg 12).
- Include **tariff escalation, discounting (NPV, IRR) and NAEPP revision scenarios**.
- Model monthly FCA and QTA adjustments to reduce the remaining bill-prediction error.
- Verify roof area, shading and shared-roof permission through a **site survey**.

---

## Repository Structure

> Adjust this section to match your actual files.

```text
.
├── README.md
├── report/
│   └── Rooftop_Solar_PV_Net_Metering_vs_Net_Billing.pdf
├── model/
│   └── techno_economic_model.xlsx
├── data/
│   ├── pvgis/            # PVGIS24 input and output screenshots
│   └── bills/            # K-Electric bills, May to Oct 2026 (Appendix A)
└── figures/
    ├── monthly_bill_comparison.png
    └── monthly_load_vs_pv.png
```

---

## How to Reproduce

1. **Get the PVGIS yield.** Open [PVGIS24](https://pvgis.com), enter 24.914° N, 67.050° E, select crystalline silicon, 1.00 kWp, triangle mounting on a flat roof, slope 29° (optimised), azimuth 0°, and losses of 1 % (cable), 2 % (inverter) and 0.5 % (PV). Record the monthly energy output.
2. **Enter the load data.** Put the monthly consumption (2,077 kWh/year) and the daytime load fraction (0.413) in the model's input sheet.
3. **Set the tariff.** Enter the A1-R slabs and fixed charges from SRO 279(I)/2026, the PHL surcharge (Rs 3.23/kWh), duty (1.5 %), sales tax (18 %), MUCT (Rs 40) and the export price (Rs 11/kWh).
4. **Run the three scenarios.** Compute no PV, net metering and net billing bills for each month using the equations in [Methodology](#methodology).
5. **Compare.** Read the annual bills, extra cost, payback and sensitivity tables from the Summary sheet.

---

## References

1. NEPRA, *National Electric Power Regulatory Authority (Prosumer) Regulations, 2026*, SRO 251(I)/2026, 9 February 2026.
2. Government of Pakistan, SRO 279(I)/2026, 12 February 2026, domestic consumer-end tariff.
3. Dawn, "Nepra pulls the plug on net-metering", 10 February 2026.
4. Geo News, "No more net metering as govt shifts to net billing".
5. Dawn, "Nepra abolishes licence requirement, fee for small solar users", 28 April 2026.
6. European Commission JRC, PVGIS24, database PVGIS-ERA5.
7. K-Electric electricity bills, May to October 2026.
8. SolarApp.pk, "1KW Solar System Price in Pakistan".

---

## License

This project was prepared for academic purposes. Unless stated otherwise, it is released under the [MIT License](LICENSE). Bill data and third-party sources remain the property of their respective owners.

---

## Author

Muhammad Yasin | Mechanical Engineering Student

- GitHub: [https://github.com/Muhammad-Yasin157](https://github.com/Muhammad-Yasin157)
- LinkedIn: [https://www.linkedin.com/in/muhammadyasin3648](https://www.linkedin.com/in/muhammadyasin3648)
- Email: [yasinbangash119@gmail.com](mailto:yasinbangash119@gmail.com)

---

## Acknowledgments

- NED University of Engineering and Technology
- Department of Mechanical Engineering

---

<div align="center">
  <sub>ME-424 Clean Energy Technology · NED University of Engineering &amp; Technology, Karachi · Fall Semester 2026</sub>
</div>
