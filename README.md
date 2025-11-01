# Market Pricing Tool v2.0 • TR Garage

A browser-only market pricing tool for compensation teams. Runs 100 percent client-side using a single `index.html`. Load CSVs, apply aging, analyze competitiveness, model structure changes, visualize results on canvas charts, and export to CSV or print-ready PDF. No servers, no libraries, no external APIs.

## Features
- Two-column layout: controls left, results right
- Four CSV uploaders with drag and drop and file validation
- Sample data baked in, edit-in-place modal, reset to default
- Assumptions form with visible aging formula
- Run analysis with loading state and error banner
- Executive summary, metric cards, two canvas charts
- Job Pricing table with compa ratios and color rules
- Structure Analysis table with midpoint to market and spreads
- Strategic Modeling and Costing: align to P50 or increase by percent, cost to minimum, percent of payroll
- Exports: results to CSV, print to PDF with clean styles
- Accessible keyboard focus and color-blind safe palette
- Everything client-side, zero external calls

## Quick Start
1. Clone the repo.
2. Open `index.html` in your browser.
3. Click **Run Market Analysis** to use the sample data.
4. Upload your own CSVs or edit the sample data in the modal.
5. Switch tabs for Summary, Detail, and Costing views.
6. Export results to CSV or print to PDF.

> Tip: No build step required. This is a single-file app.

## Data Files and Schemas
Expected column headers:

- **Job Catalog**  
  `job_code, job_profile_title`

- **Employee Data**  
  `employee_id, job_code, salary, bonus_target_percent, annual_lti_target_value`

- **Market Data**  
  `job_code, base_p25, base_p50, base_p65, base_p75, ttc_p25, ttc_p50, ttc_p65, ttc_p75, lti_p25, lti_p50, lti_p65, lti_p75, tdc_p25, tdc_p50, tdc_p65, tdc_p75`

- **Salary Structures**  
  `job_code, min_salary, mid_salary, max_salary`

## Core Calculations
- **Aging**  
  `monthsToAge = months_between(commonAgeDate, surveyDate)`  
  `agingFactor = (1 + annualRate/100) ^ (monthsToAge/12)`  
  Applied to market percentiles before comparisons.

- **Per Employee**  
  - Base compa ratio = `salary / midpoint * 100`  
  - TTC = `salary + salary * bonus_target_percent`  
  - TDC = `TTC + annual_lti_target_value`  
  - Market indices vs aged P50 for Base, TTC, TDC

- **Color Rules**  
  - Job pricing indices:  
    red if `< 90` or `> 110`, amber if `90–95` or `105–110`, green if `95–105`  
  - Structure analysis midpoint to market:  
    red if `< 90` or `> 110`, amber if `< 98` or `> 102`, green otherwise

## Strategic Modeling and Costing
- Rules
  - Align midpoints to aged Market Base P50
  - Increase midpoints by a chosen percent
- Preserve existing spreads to rebuild min and max
- Cost to minimum across impacted employees
- Output: total cost, employees impacted, cost as percent of payroll, coverage

## Exports
- **Download Results CSV** with job pricing and structure analysis sections
- **Download PDF** using browser print with clean print styles

## Accessibility
- Keyboard focus states on interactive controls
- Color-blind safe palette for chips, charts, and alerts
- Descriptive labels and aria-live regions for status

## Project Structure
- Single file app  
# market-pricing-tool
Browser-only Market Pricing Tool for Total Rewards. Single-file MVP with CSV uploads, aging, job pricing, structure analysis, costing, canvas charts, and export to CSV or PDF.
