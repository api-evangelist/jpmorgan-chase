# JPMorgan Chase GraphQL Schema

## Overview

This GraphQL schema provides a conceptual representation of JPMorgan Chase's banking and financial services APIs. JPMorgan Chase operates one of the world's largest financial services platforms, offering corporate clients and fintech partners access to payments, treasury, trade finance, FX, and market data through its developer portal at https://developer.jpmorgan.com/.

The schema covers the full scope of JPMorgan Chase's REST API surface — Payments (ACH, Wire, RTP, Faster Payments, Cross-Border), Account Services, Treasury, Trade Finance, FX, Securities, and Compliance — expressed as a unified GraphQL type system.

## Schema Source

- Developer Portal: https://developer.jpmorgan.com/
- GitHub Organization: https://github.com/jpmorganchase
- Base API URL: https://api.jpmorgan.com

## Type Categories

### Account and Balance Types

- **Account** — Core bank account entity with type, currency, balance, and transaction history
- **AccountBalance** — Real-time and available balances with pending amounts
- **AccountDetails** — Extended account metadata including interest rates and credit limits
- **BalanceHistory** — Daily opening and closing balances with credit/debit summaries

### Transaction Types

- **Transaction** — Individual account transactions with type, amount, status, and counterparty
- **TransactionDetails** — Extended transaction metadata including merchant info, FX rates, and fees
- **StatementLine** — Line items within a periodic account statement
- **Statement** — Periodic account statements with opening and closing balances

### Payment Types

- **PaymentInstruction** — Base payment instruction covering all payment rail types
- **PaymentInitiation** — Initiation record for a payment with authorization details
- **PaymentBatch** — Batch container for multiple payment instructions
- **ACHPayment** — US ACH credit and debit payments with SEC codes and trace numbers
- **WireTransfer** — Fedwire and CHIPS domestic wire transfers
- **RTPayment** — Real-Time Payments (RTP) network transactions
- **FasterPayment** — UK Faster Payments with sort code routing
- **CrossBorderPayment** — International payments with embedded FX execution
- **FundTransfer** — Internal book transfers between accounts
- **DirectDebit** — Pull payments initiated against a mandate
- **Payout** — Outbound disbursements to recipients

### Mandate and Standing Order Types

- **Mandate** — Direct debit authorization agreements between debtor and creditor
- **StandingOrder** — Recurring scheduled payment instructions

### FX and Derivatives Types

- **FXQuote** — Indicative or firm FX rate quotes with validity windows
- **FXExecution** — Executed FX deals with settlement details
- **FXSpot** — Spot FX transactions settling within two business days
- **FXForward** — Forward FX contracts with future value dates
- **FXSwap** — Combined near and far leg FX swap transactions
- **Derivative** — Generic OTC derivative instruments

### Trade Finance Types

- **TradeFinance** — Parent entity for trade finance instruments
- **LetterOfCredit** — Documentary letter of credit with shipping terms
- **BankGuarantee** — Bank-issued guarantees for trade obligations
- **Invoice** — Commercial invoices linked to payments

### Lending Types

- **Loan** — Active loan facilities with outstanding balance and payment schedule
- **LoanApplication** — Loan application and approval workflow
- **CreditLine** — Revolving credit facilities with available and utilized amounts

### Treasury and Investment Types

- **Treasury** — Aggregated treasury position including cash, investments, and FX exposures
- **Investment** — Fund and security investments with valuation
- **Securities** — Financial instrument master data
- **Bond** — Fixed-income securities with coupon and yield details
- **Settlement** — Trade settlement records
- **Custody** — Securities custody account and holdings

### Party and Counterparty Types

- **Organization** — Corporate entity with identity, tax, and address information
- **BankAccount** — Bank account with routing identifiers
- **Beneficiary** — Pre-registered payment recipients
- **Recipient** — Payout recipients with bank account details
- **Counterparty** — Trading counterparties with risk ratings
- **Remittance** — Structured payment reference and remittance information

### Banking Identifier Types

- **IBAN** — International Bank Account Number with component breakdown
- **SWIFT** — SWIFT/BIC codes for bank identification
- **RoutingNumber** — US ABA routing numbers
- **SortCode** — UK sort codes for bank branch identification

### Deposit and Withdrawal Types

- **Deposit** — Time deposits and term deposits
- **Withdrawal** — Cash and electronic withdrawals

### Compliance and Regulatory Types

- **KYC** — Know Your Customer verification records
- **RegulatoryReport** — Regulatory filings and submissions
- **ComplianceRecord** — Internal compliance tracking
- **TaxDocument** — Tax reporting documents (1099, W-8, etc.)

### API Access Types

- **APIKey** — API key credentials with scopes and expiry
- **OAuthToken** — OAuth 2.0 access and refresh token details
- **Webhook** — Event notification endpoint registrations

## Enumerations

- **TransactionType** — CREDIT, DEBIT, FEE, INTEREST, ADJUSTMENT, TRANSFER
- **PaymentStatus** — PENDING, INITIATED, PROCESSING, COMPLETED, FAILED, CANCELLED, RETURNED, REJECTED
- **MandateStatus** — ACTIVE, INACTIVE, CANCELLED, EXPIRED, SUSPENDED
- **CurrencyCode** — Major supported currencies (USD, EUR, GBP, JPY, CHF, CAD, AUD, SGD, HKD)
- **AccountType** — CHECKING, SAVINGS, MONEY_MARKET, TREASURY, ESCROW, INVESTMENT
- **LoanStatus** — ACTIVE, CLOSED, DEFAULTED, DELINQUENT, PAID_OFF
- **SettlementStatus** — PENDING, SETTLED, FAILED, REVERSED

## Query Operations

The schema exposes queries across all major domains:

- Account lookup and balance retrieval
- Transaction history and statement access
- Payment instruction status tracking (ACH, Wire, RTP, Faster, Cross-Border)
- FX quote retrieval and execution lookup
- Beneficiary, mandate, and standing order management
- Loan and credit line status
- Trade finance instrument lookup (LC, guarantees)
- Treasury position and investment valuation
- Securities and custody account access
- Organization and counterparty lookup
- Compliance and regulatory report retrieval
- Webhook management

## Mutation Operations

The schema supports mutations for:

- Payment initiation across all rails (ACH, Wire, RTP, Faster Payments, Cross-Border)
- Batch payment submission and cancellation
- Fund transfers between accounts
- Beneficiary creation and deletion
- Mandate creation and cancellation
- Standing order management
- Loan applications
- Webhook lifecycle management (create, update, delete)

## Notes

This is a conceptual GraphQL schema derived from JPMorgan Chase's published REST APIs and developer documentation. It is intended to provide a unified, graph-oriented view of the API surface for discovery and integration planning purposes. The actual production APIs are REST-based and require onboarding through the JPMorgan Chase developer portal.
