# Competitive analysis request: fill in and paste

Copy everything below the line, fill in what you know and delete what you don't. Only **Target company** is required. Then either:

- type `/comp-analysis` and paste the filled-in brief after it, or
- say: *"Use the ig-competitive-analyst agent on this brief:"* and paste it.

The agent researches the company first, then **comes back and asks you which competitors to use** before it writes the report.

---

```
COMPETITIVE ANALYSIS BRIEF

Target company:            <e.g. Superhero Markets Pty Ltd>
Website / ticker:          <e.g. superhero.com.au / ASX:XXX / private>
Sector & scale metric:     <e.g. retail investing platform – funded accounts & FUM>
Jurisdiction / currency:   <e.g. Australia, AUD>

Why we're looking:         <e.g. co-investment opportunity / competitor to IG / acquisition screen / general market view>
Transaction context:       <raise size, instrument, pre/post-money, fees, timetable – or "none">
Source documents:          <paths or links to the deck / IM / flyer / annual report – or "public sources only">

Competitors I already have in mind (optional):  <names – the agent will still propose others>
Competitors to EXCLUDE (optional):              <names and reason>
Number for the growth-strategy matrix:          <default 3>

Specific questions to answer:
- <e.g. Is the implied valuation fair versus the closest listed peer?>
- <e.g. Who is their biggest competitor and why?>

Output folder (optional):   <default reports/<company-slug>/>
Deadline (optional):        <date>
```

---

## What you get back

1. **Competitor checkpoint** (after about the first half of the work): a verified snapshot of the target, a table of 5–8 candidate peers with their scale, revenue, valuation markers and data quality, and the agent's recommendation. **You choose** the peer set and the growth-matrix competitors.
2. **Word thesis** (`<Company>_Competitive_Thesis_<date>.docx`): verdict box, peer benchmark, Porter's Five Forces, forecast and valuation stress-test, moat assessment, Buffett scorecard, growth-strategy matrix, bull/base/bear scenarios, recommendation, risk factors, sources and disclaimer.
3. **Excel audit workbook** (`<Company>_Audit_Workbook_<date>.xlsx`): README, sourced Inputs, formula-driven Historical Build & Ratios, Peer Benchmark, Audit Log and Buffett Scorecard.

Figures the agent could not source or compute are marked **N/D**. It does not estimate them.
