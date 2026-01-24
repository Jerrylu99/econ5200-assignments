# The Cost of Living Crisis: A Data-Driven Analysis

## The Problem
The official CPI is a national average.  
But students do not spend money like the “average” household. Tuition and rent take a much larger share of a student budget, so the official CPI can underestimate the real cost pressure students feel.

This project builds a custom “Student SPI” (Student Price Index) and compares it with:
- National CPI (Official CPI)
- Boston-Cambridge-Newton CPI (local inflation)
- A weighted student inflation index based on student spending patterns

---

## Methodology
### 1) Student Basket (Manual Index)
I first created a simple student basket with 2016 vs 2024 prices (example items: tuition, rent, food, streaming).  
Then I calculated inflation using a custom Python function:

\[
Inflation = \frac{Price_{2024}-Price_{2016}}{Price_{2016}} \times 100
\]

### 2) FRED API Data (Proxies)
The Federal Reserve does not track “Spotify” or “Chipotle” directly, so I used CPI proxy series from FRED:
- **CPIAUCSL**: Official CPI (benchmark)
- **CUSR0000SEEB**: Tuition, Fees, & Childcare
- **CUSR0000SEHA**: Rent of Primary Residence
- **CUSR0000SERA02**: Cable & Streaming TV
- **CUSR0000SEFV**: Food Away From Home

### 3) Normalization (Re-index to 2016 = 100)
FRED series use different base years, so raw index levels are not comparable.  
To fix this, I normalized every series to the same start date:

\[
Value\_Index_t = \frac{Value_t}{Value_{2016}} \times 100
\]

This makes all series equal to 100 in 2016 and allows fair comparison of growth over time.

### 4) Student SPI (Weighted Index)
I created a weighted “Student SPI” using a student-focused budget share:

- Tuition: 0.40  
- Rent: 0.30  
- Food Away: 0.20  
- Streaming: 0.10  

\[
Student\_SPI = \sum w_i \cdot Index_i
\]

### 5) Boston vs USA vs Student
To test whether national CPI hides local cost pressure, I also added the Boston CPI series from FRED:
- **CUURA103SA0**: Boston-Cambridge-Newton CPI

---

## Key Findings
- After normalization, student-related categories (tuition, rent, food away from home) increased faster than the official CPI.
- The weighted **Student SPI** rose faster than the national CPI, showing a clear “inflation gap.”
- Boston CPI is similar to national CPI in trend, but the **student-weighted index is consistently higher**, suggesting students experience stronger cost pressure than the average household.

---

## Visualizations
This project includes:
- Normalized CPI component trends (2016 = 100)
- Student SPI vs Official CPI with an “inflation gap” shaded area
- A “bad chart” example showing why comparing raw CPI levels without normalization is misleading
- National CPI vs Boston CPI vs Student SPI comparison

---

## Tools Used
- Python (pandas, matplotlib)
- FRED API (fredapi)
- Index theory (Laspeyres-style fixed basket logic)

---

## How to Run
1. Get a free FRED API key from the FRED website.
2. Install dependencies:
   ```bash
   pip install fredapi pandas matplotlib
