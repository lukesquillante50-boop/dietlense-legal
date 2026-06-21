# App Privacy Questionnaire + Review Notes

## PART A — App Privacy ("Data Collection")
In App Store Connect → your app → **App Privacy**. Answer "Yes, we collect data," then declare the data types below. For each: it is **linked to identity** (because it's tied to a signed-in account), **not used for tracking**, and used for **App Functionality** (some also Analytics).

Declare these data types:

| Data type | Collected? | Linked to user? | Used for tracking? | Purpose |
|---|---|---|---|---|
| **Email Address** (Contact Info) | Yes | Yes | No | App Functionality (account) |
| **User ID** | Yes | Yes | No | App Functionality (account) |
| **Health & Fitness** (your meals/nutrition/body metrics) | Yes | Yes | No | App Functionality |
| **Photos** (meal/label/product images for analysis) | Yes | Yes | No | App Functionality |
| **Other User Content** (meal descriptions, custom diets) | Yes | Yes | No | App Functionality |
| **Purchases** (subscription status) | Yes | Yes | No | App Functionality |
| **Crash Data / Diagnostics** | Yes | No | No | Analytics / App Functionality |

Key answers to remember:
- **"Do you or your partners use data for tracking?"** → **No.** (You don't show ads or share data with data brokers.)
- **"Is data linked to the user's identity?"** → **Yes** for everything except diagnostics (because it's tied to their account when signed in).
- If asked whether a third party collects data: your AI provider (OpenAI) processes images/text to return a result but does **not** use it for tracking or training — declare under App Functionality.

> Note: If you'd rather minimize the "Health & Fitness" sensitivity, you can categorize the nutrition logs under "Other User Content" instead — but "Health & Fitness" is the most accurate. Either is acceptable; just be consistent with the Privacy Policy.

---

## PART B — App Review Information (the "Notes" + demo account)
In App Store Connect → version → **App Review Information**.

**Sign-in required?** → **Yes** (provide demo account below, OR note that sign-in is optional — see notes).

**Demo Account**
Create one real account in your app before submitting and put its credentials here:
```
Email: (create a test account, e.g. appreview@dietlense.app or a Gmail you control)
Password: (the password you set)
```
> Tip: Use email/password sign-up if your app supports it, so the reviewer doesn't need your Apple/Google credentials. If the app works **without** an account, you can instead write: "No account required — all core features are usable signed out. Sign-in only enables cloud sync."

**Notes for Reviewer** (paste this):
```
DietLens is a nutrition tracker. Core features (manual logging, barcode scan, and barcode-based food rating) work without an account and offline.

AI features (photo meal scan, nutrition-label scan, AI food rating, describe-a-meal) send the image or text to our backend and then to OpenAI to estimate nutrition. These require a network connection.

Free tier: unlimited manual logging and barcode scanning, plus 3 AI scans per day. Paid tiers (Plus/Pro, auto-renewing) unlock unlimited AI scans, micronutrients, meal plans, cloud sync, Family Mode, and custom diets. A 3-day free trial is offered on each subscription.

To test AI scans without limits, the provided demo account has premium enabled. To test a subscription purchase, use a sandbox tester account in StoreKit.

Account deletion is available in-app at Settings → Account → Delete Account.

Privacy Policy: (your URL)
Terms of Use: (your URL)
```

**Contact info:** your name, phone, and email (luke.squillante50@gmail.com).

---

## PART C — Things reviewers commonly reject for (pre-check)
- ✅ **Account deletion in-app** — you have it (Settings → Account → Delete Account). Required by Apple 5.1.1(v).
- ✅ **Subscriptions show price + duration + Terms/Privacy links** on the paywall — confirm the paywall shows these before purchase.
- ⚠️ **Privacy Policy + Terms URLs must be live** before you submit (host the two HTML files).
- ⚠️ **Backend must be deployed** (`vercel --prod`) or AI scans fail during review → rejection. Test on a real device against the production backend first.
- ⚠️ **Functional restore** — you have a Restore Purchases button; confirm it works in sandbox.
