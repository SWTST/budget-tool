## Suggested Budget Categories

**Parent Categories**
INC, HOU, UTL, FOO
TRN, INS, HLT, SUB
SHP, ENT, SAV, INV
DBT, GFT, EDU, PET
HOL, TRF, MSC

```
--SQL
INSERT INTO [dbo].[BudgetCategoryParent] ([Code], [CategoryID], [Name])
VALUES
('INC',  1, 'Income'),
('HOU',  2, 'Housing'),
('UTL',  3, 'Utilities'),
('FOO',  4, 'Food'),
('TRN',  5, 'Transport'),
('INS',  6, 'Insurance'),
('HLT',  7, 'Health'),
('SUB',  8, 'Subscription'),
('SHP',  9, 'Shopping'),
('ENT', 10, 'Entertainment'),
('SAV', 11, 'Saving'),
('INV', 12, 'Investment'),
('DBT', 13, 'Debt'),
('GFT', 14, 'Gift'),
('EDU', 15, 'Education'),
('PET', 16, 'Pets'),
('HOL', 17, 'Holiday'),
('TRF', 18, 'Transfers'),
('MSC', 19, 'Miscellaneous');
```

**Income**
INC_SAL Salary & wages
INC_BEN Benefits
INC_INT Interest
INC_REF Refunds/Rebates

**Housing & Utilities**
HOU_RENT Rent / Mortgage
HOU_CTAX Council Tax
UTL_ELEC Electricity
UTL_GAS Gas
UTL_WATR Water
UTL_BBND Broadband
UTL_MOB Mobile
UTL_TVLC TV Licence

**Food**

FOO_GROC Groceries
FOO_EAT Eating out / Takeaway / Coffee

**Transport**

TRN_FUEL Fuel
TRN_PUB Public transport
TRN_PARK Parking & tolls
TRN_MAIN Vehicle maintenance
TRN_MOT MOT / Vehicle tax

**Insurance**

INS_HOME Home/Contents
INS_AUTO Car
INS_LIFE Life/Health/Travel (use per need)

**Health & Fitness**

HLT_PHAR Prescriptions/Pharmacy
HLT_DENT Dentist/Optician
HLT_GYM Gym/Fitness

**Subscriptions & Media**

SUB_STRM Streaming (Netflix/Spotify/etc.)
SUB_SOFT Software/Cloud storage
SUB_GAME Gaming

**Shopping & Home**

SHP_CLOT Clothing
SHP_ELEC Electronics
SHP_HOME Home & garden

**Entertainment & Hobbies**

ENT_EVT Events/Days out
ENT_HOB Hobbies (add ENT_CLMB if you want a Climbing subcat!)

**Savings & Investments**

SAV_XFER Savings transfers
INV_ISA Stocks & Shares ISA
INV_GEN General investments
INV_PEN Pension contributions

**Debt & Fees**

DBT_INT Credit card interest
DBT_FEES Bank/FX/ATM fees

**Gifts, Charity & Education**

GFT_CHR Gifts & Charity
EDU_CRS Courses/Certs/Books

**Pets**

PET_FOOD Food/Accessories
PET_VET Vet/Insurance

**Holidays & Travel**

HOL_FLT Flights
HOL_HTL Hotels
HOL_ACT Activities
HOL_INS Travel insurance

**Transfers (neutral – exclude from spend)**

TRF_IN Self-to-self incoming (FPI/BGC from your other accounts)
TRF_OUT Self-to-self outgoing (FPO/SO to your other accounts)

**Miscellaneous**

MSC_ONE One-off / Uncategorized (temporary holding)

```
--SQL
INSERT INTO [dbo].[BudgetCategory]
    ([CategoryID],[ParentCategoryID],[Code],[Name],
     [IsIncome],[IsTransfer],[IsFixed],[SortOrder],[IsActive])
VALUES
-- Income
(101, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'INC'),
 'INC_SAL', 'Salary & wages', 1, 0, 1, 101, 1),
(102, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'INC'),
 'INC_BEN', 'Benefits', 1, 0, 1, 102, 1),
(103, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'INC'),
 'INC_INT', 'Interest', 1, 0, 0, 103, 1),
(104, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'INC'),
 'INC_REF', 'Refunds/Rebates', 1, 0, 0, 104, 1),

-- Housing
(105, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'HOU'),
 'HOU_RENT', 'Rent / Mortgage', 0, 0, 1, 105, 1),
(106, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'HOU'),
 'HOU_CTAX', 'Council Tax', 0, 0, 1, 106, 1),

-- Utilities
(107, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'UTL'),
 'UTL_ELEC', 'Electricity', 0, 0, 1, 107, 1),
(108, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'UTL'),
 'UTL_GAS', 'Gas', 0, 0, 1, 108, 1),
(109, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'UTL'),
 'UTL_WATR', 'Water', 0, 0, 1, 109, 1),
(110, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'UTL'),
 'UTL_BBND', 'Broadband', 0, 0, 1, 110, 1),
(111, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'UTL'),
 'UTL_MOB', 'Mobile', 0, 0, 1, 111, 1),
(112, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'UTL'),
 'UTL_TVLC', 'TV Licence', 0, 0, 1, 112, 1),

-- Food
(113, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'FOO'),
 'FOO_GROC', 'Groceries', 0, 0, 0, 113, 1),
(114, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'FOO'),
 'FOO_EAT', 'Eating out / Takeaway / Coffee', 0, 0, 0, 114, 1),

-- Transport
(115, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'TRN'),
 'TRN_FUEL', 'Fuel', 0, 0, 0, 115, 1),
(116, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'TRN'),
 'TRN_PUB', 'Public transport', 0, 0, 0, 116, 1),
(117, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'TRN'),
 'TRN_PARK', 'Parking & tolls', 0, 0, 0, 117, 1),
(118, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'TRN'),
 'TRN_MAIN', 'Vehicle maintenance', 0, 0, 0, 118, 1),
(119, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'TRN'),
 'TRN_MOT', 'MOT / Vehicle tax', 0, 0, 0, 119, 1),

-- Insurance
(120, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'INS'),
 'INS_HOME', 'Home/Contents insurance', 0, 0, 1, 120, 1),
(121, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'INS'),
 'INS_AUTO', 'Car insurance', 0, 0, 1, 121, 1),
(122, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'INS'),
 'INS_LIFE', 'Life/Health/Travel insurance', 0, 0, 1, 122, 1),

-- Health & Fitness
(123, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'HLT'),
 'HLT_PHAR', 'Prescriptions/Pharmacy', 0, 0, 0, 123, 1),
(124, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'HLT'),
 'HLT_DENT', 'Dentist/Optician', 0, 0, 0, 124, 1),
(125, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'HLT'),
 'HLT_GYM', 'Gym/Fitness', 0, 0, 1, 125, 1),

-- Subscriptions & Media
(126, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'SUB'),
 'SUB_STRM', 'Streaming (Netflix/Spotify/etc.)', 0, 0, 1, 126, 1),
(127, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'SUB'),
 'SUB_SOFT', 'Software/Cloud storage', 0, 0, 1, 127, 1),
(128, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'SUB'),
 'SUB_GAME', 'Gaming subscriptions', 0, 0, 1, 128, 1),

-- Shopping & Home
(129, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'SHP'),
 'SHP_CLOT', 'Clothing', 0, 0, 0, 129, 1),
(130, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'SHP'),
 'SHP_ELEC', 'Electronics', 0, 0, 0, 130, 1),
(131, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'SHP'),
 'SHP_HOME', 'Home & garden', 0, 0, 0, 131, 1),

-- Entertainment & Hobbies
(132, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'ENT'),
 'ENT_EVT', 'Events/Days out', 0, 0, 0, 132, 1),
(133, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'ENT'),
 'ENT_HOB', 'Hobbies', 0, 0, 0, 133, 1),

-- Savings & Investments
(134, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'SAV'),
 'SAV_XFER', 'Savings transfers', 0, 0, 1, 134, 1),
(135, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'INV'),
 'INV_ISA', 'Stocks & Shares ISA', 0, 0, 1, 135, 1),
(136, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'INV'),
 'INV_GEN', 'General investments', 0, 0, 1, 136, 1),
(137, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'INV'),
 'INV_PEN', 'Pension contributions', 0, 0, 1, 137, 1),

-- Debt & Fees
(138, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'DBT'),
 'DBT_INT', 'Credit card interest', 0, 0, 0, 138, 1),
(139, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'DBT'),
 'DBT_FEES', 'Bank/FX/ATM fees', 0, 0, 0, 139, 1),

-- Gifts, Charity & Education
(140, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'GFT'),
 'GFT_CHR', 'Gifts & Charity', 0, 0, 0, 140, 1),
(141, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'EDU'),
 'EDU_CRS', 'Courses/Certs/Books', 0, 0, 0, 141, 1),

-- Pets
(142, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'PET'),
 'PET_FOOD', 'Pet food/Accessories', 0, 0, 1, 142, 1),
(143, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'PET'),
 'PET_VET', 'Vet/Insurance', 0, 0, 0, 143, 1),

-- Holidays & Travel
(144, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'HOL'),
 'HOL_FLT', 'Flights', 0, 0, 0, 144, 1),
(145, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'HOL'),
 'HOL_HTL', 'Hotels', 0, 0, 0, 145, 1),
(146, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'HOL'),
 'HOL_ACT', 'Holiday activities', 0, 0, 0, 146, 1),
(147, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'HOL'),
 'HOL_INS', 'Travel insurance', 0, 0, 0, 147, 1),

-- Transfers (neutral)
(148, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'TRF'),
 'TRF_IN', 'Self-to-self incoming', 0, 1, 0, 148, 1),
(149, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'TRF'),
 'TRF_OUT', 'Self-to-self outgoing', 0, 1, 0, 149, 1),

-- Miscellaneous
(150, (SELECT CategoryID FROM dbo.BudgetCategoryParent WHERE Code = 'MSC'),
 'MSC_ONE', 'One-off / Uncategorized', 0, 0, 0, 150, 1);
```