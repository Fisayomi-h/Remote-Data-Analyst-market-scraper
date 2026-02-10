# Web Scraping Nigeria’s Personal Loan Market

## Objective

This project demonstrates how web scraping can be used to create structured datasets from unstructured web content in order to answer real business questions.

**Business question addressed:**

How transparent are Nigerian personal loan providers about pricing and loan terms before a customer applies? How other financial services can compete?

There is no public dataset that answers this question.  
The data exists only across individual lender websites.  
In a competitive financial landscape, interest rates and terms (fees, penalties, collateral) change constantly.  
For a business, staying competitive requires real-time monitoring.  
For a consumer, finding the true cost of a loan is often buried behind marketing walls.

---

## Project Setup & Structure

This project is designed to scrape and structure loan information from multiple Nigerian financial service providers in order to evaluate pricing transparency across the market.

Before scraping begins, the required libraries and scraping scope are defined.

### 1. Library Imports

Each library plays a specific role in the scraping and analysis workflow:

![Library Imports](https://github.com/user-attachments/assets/b1f0b6ff-f07e-4fa4-859a-b5d1ac1af8b9)

- **requests** — Fetches web page content from lender websites.  
- **BeautifulSoup (bs4)** — Parses HTML pages and extracts readable text for analysis.  
- **pandas** — Structures scraped data into a DataFrame for analysis and export.  
- **re (Regular Expressions)** — Identifies patterns such as interest rates and pricing terms within unstructured text.  
- **time** — Adds delays between requests to ensure responsible and stable scraping.  
- **datetime** — Records the scrape date for traceability and time-based analysis.  

---

### 2. Data Collection Phases

The scraping scope is intentionally split into two phases to reflect how the Nigerian credit market is structured:

- **Phase 1 — Banks & Microfinance Banks**  
- **Phase 2 — Fintechs, Fintech Banks & Government-Backed Credit**  

---

### 3. Detecting Interest Rate Disclosure

This regex identifies explicit pricing disclosure.  

If no match is found:  

- Pricing is either hidden  
- Or only revealed after application  

This distinction is critical for transparency analysis.

![Interest Rate Regex](https://github.com/user-attachments/assets/279e42a7-217c-4185-bc66-221808393760)

---

### 4. Translating Text into Business Signals

![Business Signals](https://github.com/user-attachments/assets/dd3d7145-3ea1-49e1-afd1-640f0ec1a4a9)

For every lender, the script calls a reusable scraping function that analyzes the page for key transparency signals such as interest rate disclosure, tenure, fees, penalties, and eligibility requirements.  

A short delay is added between requests to ensure responsible scraping. The results are aggregated into a Pandas DataFrame and exported as a CSV file, transforming unstructured web pages into a reusable dataset that can support:

- Market analysis  
- Compliance reviews  
- Data-driven business decisions  

---

### 5. Output for Analysis

![Output 1](https://github.com/user-attachments/assets/4bbec748-15a9-4f73-90f1-d624dfbdcdd9)  
![Output 2](https://github.com/user-attachments/assets/e3ecbaa1-7cec-42a3-ac0e-e6207a467ec1)  
![Output 3](https://github.com/user-attachments/assets/19c5695c-e017-4406-80f1-7e1d18c9cd1f)  

---

### 6. Insights

#### 1. Interest Rate Transparency Is Inconsistent

- Only a subset of lenders clearly disclose interest rates on their public pages.  
- Traditional banks show mixed transparency:  
  - Some banks (e.g., First Bank, Stanbic IBTC, Fidelity) clearly disclose rates.  
  - 58% of traditional banks scraped (including Access, UBA, GTBank, and Wema) did not disclose interest rates on their primary product pages.  
  - Others (e.g., GTBank, Wema Bank, FCMB) do not publish interest rates upfront.  
- Fintech lenders are generally more transparent, with platforms like Carbon, FairMoney, Credit Direct, CashX, and Kuda clearly stating rates or ranges. They have near 100% disclosure rates.  
- Government-backed programs (YouthCred, CrediCorp) largely avoid explicit pricing disclosure, suggesting pricing may be policy-driven or determined during application.  

**Finding:** Access Bank returned an "Error," likely due to dynamic redirects to Rate Guides not indexed on the main landing page—a common tactic to prevent easy price comparison.  

**Business implication:** Customers cannot reliably compare loan costs across providers without starting an application, increasing friction and reducing informed decision-making. Fintechs are winning the Trust Economy by reducing the time-to-decision for the user. They compete on Speed and Clarity rather than just the lowest rate.

#### 2. Salary-Based Lending Dominates

- Salary requirements appear frequently across banks and fintechs.  
- Most bank loans explicitly require:  
  - Salary accounts  
  - Proof of income  
- Fintech lenders are more flexible, but many still implicitly depend on income signals or transaction history.  

**Business implication:** The market is strongly skewed toward formally employed borrowers, leaving informal workers underserved.

#### 3. Collateral Is Less Common, But Not Absent

- Collateral requirements are less visible than salary requirements but still present.  
- Banks and microfinance banks occasionally require collateral or guarantees.  
- Fintechs mostly avoid explicit collateral but rely on alternative risk controls (limits, penalties, short tenures).  

**Business implication:** Risk management has shifted from physical collateral to behavioral and data-driven controls, especially among fintechs.

#### 4. Data-Driven Recommendations for Managers

- **For Product Managers:** To compete with Fintechs, Commercial Banks should move their "Rate Calculators" in front of the login wall.  
- **For Risk Analysts:** The data shows that "Quick Loans" (EZ Cash, FastCash) often have 2-4% higher monthly rates than standard salary loans but higher engagement due to transparency.  

---

### Key Takeaway for Businesses and Analysts

This analysis shows that valuable market intelligence often exists in fragmented, unstructured, and inconsistent formats.  

**Web scraping bridges this gap** by turning scattered public disclosures into structured datasets that enable:  

- Competitive benchmarking  
- Pricing transparency analysis  
- Risk and compliance monitoring  
- Better product and policy decisions  

This is a practical example of how **data skills can answer real business questions**, even when no ready-made dataset exists.

