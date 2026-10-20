# Waterfall Engine

Agency CMO analytics: class-level cashflows, price/yield, WAL and duration for Ginnie Mae, Fannie Mae and Freddie Mac REMICs, modelled from each deal's own payment rules.

## What it does

- **Look up any class by CUSIP** and see its deal, group, current balance, factor and collateral.
- **Project class cashflows** month by month on the agency's payment dates: principal, interest, accretion and balances.
- **Price and yield**: price from yield, yield from price, discount margin, WAL, modified and Macaulay duration, convexity.
- **Floating and inverse coupons** set from your own index paths (SOFR and others), with each class's caps, floors and multipliers applied.
- **Your own prepayment assumptions**: a flat CPR or PSA, a CPR or SMM vector, different speeds for each collateral pool, or your own prepayment model.
- **Re-REMICs**: groups backed by other deals' classes are projected through every layer down to the pools underneath.
- **Scenario runs**: build a deal once, then run many speed and rate scenarios quickly.

## How it works

Each deal's principal and interest rules are modelled from that deal's own structure: sequential, pro rata, PAC and support schedules, accrual classes, exchangeable classes and notional IOs. Collateral is followed pool by pool from the agencies' monthly factor files, so projections start from current balances.

## Repository layout

```
waterfall-engine/
├── api/                    Python client API
│   ├── deal, group, class      look up by CUSIP; deal pages and summaries
│   ├── collateral              pools, strata, subgroups, re-REMIC look-through
│   ├── speeds                  CPR / PSA / SMM inputs, by pool or by group
│   ├── waterfall               plain-English payment rules for each group
│   └── cashflow/
│       ├── project             period-by-period projection
│       ├── classflows          class cashflow tables
│       ├── calendar            agency payment and accrual dates
│       ├── market              index paths (SOFR and others)
│       ├── arm                 ARM collateral resets
│       └── price_yield         price, yield, DM, WAL, duration, convexity
├── engines/                one for each agency's deal structures
│   ├── ginnie
│   ├── fannie
│   └── freddie
├── dealdb/                 as-issued deal facts: classes, groups, pools, coupon formulas
├── statedb/                monthly updates from agency factor files
│   ├── factors, pools          current balances and pool data
│   ├── speeds                  measured prepayment speeds
│   └── multifamily             Ginnie multifamily loans
├── examples/
└── tests/
```

*Source is private. This shows how the engine is organised.*

## Status

In active development. Access is by arrangement. Get in touch if you would like to try it.

## Contact

logic@waterfallengine.com

---

Waterfall Engine is independent and is not affiliated with or endorsed by Ginnie Mae, Fannie Mae or Freddie Mac.
