# K4SRU Python Porting Plan

## Phase 1: Setup & Core Models (Days 1-2)
- [ ] Create Python project structure
- [ ] Define data models (dataclasses):
  - Trade, SecurityHolding, CurrencyHolding
  - SecuritySale, CurrencySale
  - K4Blankett, K4Rad
- [ ] Implement Money/Currency handling

## Phase 2: Import Modules (Days 3-5)
- [ ] Port Pareto CSV parser
- [ ] Port IBKR CSV parser  
- [ ] Port Avanza CSV parser
- [ ] Port Saxo Excel parser
- [ ] Test each parser independently

## Phase 3: Core Business Logic (Days 6-8)
- [ ] FinancialYear & transaction processing
- [ ] Currency conversion logic
- [ ] Position tracking (FIFO)
- [ ] Merge/consolidation logic

## Phase 4: Output Generation (Days 9-10)
- [ ] K4 form generation
- [ ] SRU file format writer
- [ ] Excel output writer
- [ ] Validation logic

## Phase 5: Testing & Migration (Days 11-14)
- [ ] Unit tests for critical logic
- [ ] Integration test with real data (2023/2024)
- [ ] Compare outputs with Java version
- [ ] Documentation & README update

## AI-Assisted Approach

Use AI to:
1. Translate individual Java classes → Python (one at a time)
2. Review and fix logic errors
3. Optimize with pandas where appropriate
4. Generate test cases

Manual oversight needed for:
- Business logic verification
- SRU format compliance
- Swedish tax rule accuracy

## Suggested Python Stack

```
pandas          # Excel/CSV, data manipulation
openpyxl        # Excel writing
dataclasses     # Models
decimal         # Precise money calculations
logging         # Built-in
pytest          # Testing
```

## Quick Start Command

```bash
# New project structure
mkdir k4sru-python
cd k4sru-python
python -m venv venv
source venv/bin/activate
pip install pandas openpyxl pytest
```

## Risk Mitigation

1. **Keep Java version** - Use as reference and validation
2. **Port incrementally** - One broker at a time
3. **Validate with historical data** - Compare 2023/2024 outputs
4. **Test edge cases** - Currency conversions, short sales, etc.

## Alternative: Hybrid Approach

If you want to start small:
1. Port just the Saxo parser to Python first (your current branch)
2. Keep rest in Java temporarily
3. Use data file interchange
4. Gradually migrate other components

## Next Steps

1. Decide: Full port vs. hybrid approach
2. Create Python project skeleton
3. Start with simplest parser (Pareto or Avanza)
4. Build confidence before core logic
