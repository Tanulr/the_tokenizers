# IngrediWise: Your Personalized AI Companion for Food, Skincare, Makeup, and Everyday Products

**Team name:** TBD

## 1. Problem

Consumers with food allergies, skin conditions, autoimmune conditions, ingredient sensitivities, or specific dietary and lifestyle goals struggle to determine whether the products they buy are suitable for their individual needs. This applies to the food they eat and to everything that touches their skin: skincare, makeup, and everyday products such as soaps, shampoos, deodorants, and laundry detergents. While shopping at retailers such as Walmart, Target, and beauty stores, they must manually examine ingredient lists, decipher unfamiliar chemical names, research potential allergens or irritants, and compare products against their personal health conditions and preferences.

In food, this means spotting hidden allergens, additives, and nutritional content that conflicts with a diet or health condition. For products that touch the skin, it means decoding long ingredient lists written in technical INCI names (for example, "parfum" for fragrance or "tocopherol" for vitamin E) to find fragrances, preservatives, dyes, pore-clogging oils, or active ingredients that may cause allergic reactions, irritation, or breakouts. A person with sensitive skin may carefully choose a fragrance-free moisturizer, only to have a reaction caused by their foundation, shampoo, or laundry detergent. Existing product labels and generic safety ratings rarely explain how a particular product relates to an individual's unique health profile, making informed purchasing decisions time-consuming and uncertain.

## 2. User

Our primary users are health-conscious shoppers, particularly individuals managing food allergies, skin conditions such as eczema, rosacea, or acne-prone and sensitive skin, autoimmune conditions, ingredient sensitivities, or dietary goals. For example, someone with a food allergy may need to identify hidden allergens in packaged foods, while someone with eczema may want to avoid fragranced moisturizers that irritate their skin. Similarly, a shopper following a keto or weight-loss diet may want personalized nutritional insights, someone with acne-prone skin may want potentially pore-clogging ingredients flagged in a new foundation or sunscreen, and someone with contact dermatitis may want to avoid certain preservatives in their shampoo and body wash.

These categories also overlap in ways shoppers often miss. A person with a tree-nut allergy, for instance, may want to know that a body lotion contains sweet almond oil, just as they would check a granola bar for almonds. Someone sensitive to fragrance needs to check their moisturizer, lipstick, deodorant, and detergent, not just one of them.

Unlike existing applications that primarily provide generic ingredient ratings, nutritional scores, or analysis limited to a single product category, IngrediWise aims to **evaluate food, skincare, makeup, and everyday skin-contact products using one personalized health and lifestyle profile**. A sensitivity entered once is checked everywhere it could appear. Users would choose it to reduce the effort of researching products individually and to receive explanations relevant to their own needs. We envision a freemium model with basic product scanning available for free and advanced personalized analysis through a subscription. We still need to validate user trust, willingness to pay, and whether shoppers find cross-category personalization more valuable than existing specialized applications.

## 3. MVP

The MVP will be a mobile-friendly web application that serves as an AI-powered shopping companion for four product categories:

- **Food:** packaged food and beverages.
- **Skincare:** facial and body skincare, including cleansers, moisturizers, serums, sunscreens, and body lotions.
- **Makeup:** foundation, concealer, powder, lipstick and lip products, eye makeup, and makeup removers.
- **Everyday skin-contact products:** soaps and body washes, shampoos and conditioners, deodorants, hand sanitizers, laundry detergents, fabric softeners, and dishwashing liquids.

Users begin by creating a personalized profile containing their allergies, known ingredient sensitivities, relevant health conditions, dietary restrictions, skin type and skin concerns (such as dry, oily, sensitive, acne-prone, eczema, or rosacea), and lifestyle goals such as weight loss, keto, or high-protein nutrition. While shopping, users scan a product barcode or photograph its ingredient label, after which the application retrieves or extracts product information and analyzes its ingredients against the user's profile.

The application then generates a **personalized product assessment**:

- **For food products,** it highlights potential allergens, ingredients that conflict with dietary restrictions, user-specified health-related concerns, nutritional benefits, and compatibility with personal goals.
- **For skincare and makeup,** it highlights potential allergens, fragrance components, preservatives, dyes and other commonly reported irritants, ingredients that may be pore-clogging for acne-prone users, and compatibility with the user's skin type and concerns. Products used near the eyes or on the lips are noted where relevant.
- **For everyday skin-contact products,** it highlights fragrances, preservatives, dyes, and other commonly reported irritants, taking into account whether the product is rinsed off (such as shampoo), left on the skin (such as deodorant), or touches the skin indirectly (such as detergent residue on clothing).

For example, the same fragranced moisturizer or laundry detergent might receive a fragrance-related caution for someone with eczema but no such personalized flag for a shopper without that sensitivity. Similarly, a packaged snack might be assessed against a user's dietary goals, a foundation might be flagged for a pore-clogging ingredient for an acne-prone user, and a body lotion might be flagged for a nut-derived oil because of the same user's food allergy. The application will translate technical ingredient names into plain language, explain which ingredients influenced its assessment, distinguish confirmed matches from uncertain concerns, and provide a simple summary to support purchasing decisions.

**Not in the MVP:** Products that rarely touch the skin, such as surface and bathroom cleaners, air fresheners, and pesticides (possible future expansion); medical or dermatological diagnosis; predictions of skin reactions or autoimmune flare-ups; automated purchasing; retailer checkout integrations; and personalized product recommendations requiring extensive medical records. The MVP will focus on identifying documented ingredients and matching them against user-provided sensitivities and established ingredient information, rather than making unsupported medical claims.

## 4. Data

We will use publicly available product databases, primarily **Open Food Facts** for food and beverages and **Open Beauty Facts** for skincare, makeup, and personal care products, supplemented by ingredient labels and manufacturer product information. For laundry detergents and other household products, which have limited open database coverage, we will rely on manufacturer ingredient disclosures and label photos. We will build curated ingredient references for each category:

- **Food:** major food allergens, common additives, and their alternate names.
- **Skincare, makeup, and personal care:** INCI ingredient names mapped to common names and synonyms, recognized fragrance allergens, preservatives and dyes known to cause reactions, and commonly reported irritants and pore-clogging ingredients, each tagged with how well supported the concern is.
- **Laundry and household products:** common fragrances, preservatives, enzymes, optical brighteners, and surfactants reported to cause skin irritation.

Synthetic user profiles will represent different allergies, sensitivities, skin types and concerns, health conditions, and lifestyle goals during testing.

## 5. Models and APIs

- **LLM:** Lightweight language model for ingredient interpretation and personalized explanations.
- **Vision/OCR:** Extract ingredient lists and product information from photographs, including small-print and curved packaging on skincare, makeup, and personal care products.
- **Retrieval:** Public product databases and curated ingredient references for each category, including INCI synonym mapping.
- **Estimated cost:** Approximately $0.001 to $0.02 per product assessment, to be validated during development.

## 6. Evaluation

We will test the application using a balanced set of food, skincare, makeup, and everyday skin-contact products and synthetic user profiles, comparing generated assessments against verified ingredient labels and manually established matching rules. Each measure will be reported separately for each category so weaknesses in one category are not hidden by the others.

| Measure | Target |
| --- | --- |
| Known allergen/sensitivity match recall | ≥ 99% |
| Ingredient extraction accuracy | ≥ 95% |
| Ingredient name normalization (INCI and synonym mapping) | ≥ 95% |
| Personalized rule-matching accuracy | ≥ 90% |
| Product assessment response time | Under 5 seconds |

## 7. Risks

| Risk | Fallback |
| --- | --- |
| Incomplete product databases or ingredient labels (coverage is likely thinner for skincare and makeup than food, and thinnest for laundry and household products) | Allow users to photograph and manually verify product labels |
| Incomplete ingredient disclosure on some products (for example, fragrance listed as a single ingredient, or partial lists on detergents) | Flag undisclosed or grouped ingredients as an uncertain concern for users with related sensitivities |
| Technical or inconsistent ingredient names on skincare, makeup, and personal care labels | Maintain a curated INCI and synonym dictionary; flag unrecognized ingredients as uncertain rather than ignoring them |
| Unsupported medical claims or incorrect health assessments | Restrict assessments to evidence-supported concerns and user-defined sensitivities |
| Skin reactions vary widely between individuals | Avoid "safe for your skin" claims; present flags as potential concerns and encourage patch testing for new skincare and makeup products |
| AI hallucinations or incorrect ingredient interpretation | Use deterministic matching and curated ingredient references |
| Sensitive user health information and privacy | Minimize stored information and provide profile deletion controls |
