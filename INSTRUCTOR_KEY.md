# Instructor Key — Assignment 2.2

## Planted Workbook Defect
The workbook correctly converts suction and discharge pressure from kPa to psi in the first two chain steps. The differential-pressure step divides the already-converted pressure difference by the kPa-per-psi conversion factor a second time. This is a duplicate conversion.

## Correct Chain
1. suction kPa → psi
2. discharge kPa → psi
3. differential psi = discharge psi - suction psi
4. head ft = differential psi × 2.31 / SG
5. hydraulic hp = flow gpm × head ft × SG / 3960
6. efficiency fraction = efficiency % / 100
7. brake hp = hydraulic hp / efficiency fraction

## Required Validation Rules
Use the workbook Operating Limits sheet as the grading basis.

### Individual
- suction pressure >= 0
- discharge pressure >= 0
- flow > 0
- rated flow > 0
- SG > 0
- efficiency > 0 and <= 100

### Combination
- discharge pressure > suction pressure
- requested flow <= rated flow

## Strong Evidence
Students should prove rejection with pytest.raises and should test at least one known-correct reference case end-to-end through the unit boundary.

## Suggested Code-Defense Questions
1. Point to the only place pressure conversion occurs.
2. What unit is differential_pressure in?
3. Show the test that would catch a second pressure conversion.
4. Show two pressures that are individually legal but invalid together.
5. Explain why flow > rated flow is a combination rule.
6. Change one supported range and update the test live.
