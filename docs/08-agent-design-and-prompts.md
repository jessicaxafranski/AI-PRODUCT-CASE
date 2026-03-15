## 8. Agent Design & Prompts

This section documents the AI agent behaviors and prompts used to experiment with housing opportunity analysis and discovery.

---

### 8.1 AI Housing Opportunity Agent (Listing-Level Analysis)

The `agente01_test` document defines an AI agent that evaluates individual housing listings and scores them against a tenant profile.

#### Conceptual Architecture

```text
Tenant Profile
  ↓
AI Housing Agent
  ↓
Housing Source Monitor (Idealista, Badi, Facebook, Instagram)
  ↓
Listing Collector
  ↓
AI Listing Analyzer
  ↓
Matching Engine
  ↓
Opportunity Feed
```

The agent:

- Extracts listing attributes:
  - Price
  - Location
  - Accommodation type (room, shared apartment, studio, apartment)
  - Empadronamiento compatibility (yes, negotiable, no, unknown)
  - Minimum / maximum stay
  - Number of tenants allowed
  - Trust signals and risk indicators
- Compares them against a tenant profile:
  - Budget range
  - Preferred location
  - Empadronamiento requirement
  - Accommodation type
  - Move-in date
  - Minimum stay preference
  - Number of tenants
- Outputs:
  - Compatibility score (0–100)
  - Short explanation
  - Extracted signals
  - Potential risks or uncertainties

The agent prioritizes listings that:

1. Allow empadronamiento  
2. Match the tenant’s budget  
3. Are recently posted  
4. Match accommodation type  
5. Show signals that the landlord is likely to respond  

---

### 8.2 AI Housing Discovery Agent (Empadronamiento-Oriented Search)

The `PROMPT_AI` document defines an AI Housing Discovery Agent focused on scanning listings for empadronamiento signals across multiple platforms.

The agent:

- Searches listings on:
  - Idealista
  - Badi
  - Fotocasa
  - Habitaclia
  - Facebook housing groups
  - Instagram housing pages
- Identifies keywords related to empadronamiento, such as:
  - empadronamiento  
  - empadronar  
  - se puede empadronar  
  - empadronamiento posible / permitido  
  - no empadronamiento / sin empadronamiento  
- Classifies each listing into:
  - Empadronamiento Allowed  
  - Empadronamiento Negotiable  
  - Empadronamiento Not Allowed  
  - Empadronamiento Unknown  
- Returns only listings where:
  - Empadronamiento Allowed, or  
  - Empadronamiento Negotiable  

For each listing, it extracts:

- Price  
- Location  
- Accommodation type (room / apartment / studio)  
- Minimum stay duration  
- Any mention of couples or tenant restrictions  

Output format:

- Listing Title  
- Platform  
- Price  
- Location  
- Empadronamiento Status  
- Relevant Text Detected  
- Link  

The agent focuses on listings located in Barcelona.

