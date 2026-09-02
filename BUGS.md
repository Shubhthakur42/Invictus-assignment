# Bugs found

Add one section per issue. Bug 1 is filled in to show the format — fix it, then write what you changed. Copy the blank template for the rest.

Keep this file in the repo and **commit it** with your fixes.

---

## Bug 1

**How to reproduce:** Open the app. The expense list says “Newest first”. The first row is Wine (7 Mar). Board game (15 Mar) is further down.

**What is wrong:** The list is showing oldest expenses first. Newest should be at the top.

**What I changed:** Changed the Sorting order to descending ordert to show newest expence first.

---

## Bug 2

**How to reproduce:** Open the Paid by filter and select a member

**What is wrong:**Expenses paid by the selected member is not displaying because the select value was a string while expense paidBy values were numbers.

**What I changed:** Before comparing them in the Paid by filter I normalized both values to numbers before comparing them in the Paid by filter.

---

## Bug 3

**How to reproduce:** Apply a filter or rely on the sorted expense list, then edit or delete an expense that is not at the same index in the original expense array.

**What is wrong:** The UI used the filtered/sorted array index when updating or deleting the original expense array, which could modify or delete a different expense.

**What I changed:** Changed expense update and deletion to use the expense's unique ID instead of an array index.

## Bug 4

**How to reproduce:** Add or inspect an expense where a member pays more than their own share.

**What is wrong:** Positive balances were displayed as money the member owed, while negative balances were displayed as money owed to the member.

**What I changed:** Corrected the balance labels so a positive balance means the member is owed money and a negative balance means the member owes money.

## Bug 5

**How to reproduce:** Add an expense where the payer is not included in the split, such as a $600 cab paid by Aisha and shared only by Ben and Carlos.

**What is wrong:** The payer was credited with the full amount and then incorrectly charged another portion of the same expense.

**What I changed:** Removed the extra deduction so a payer who is not part of the split receives the full amount they paid back.

## Bug 6

**How to reproduce:** Add a $100 expense and split it equally between three people.

**What is wrong:** Each person received $33.33, causing the shares to total $99.99 instead of the original $100.

**What I changed:** Changed equal-split rounding to work in cents and distribute any remainder so the shares always total exactly to the original expense.

## Bug 7

**How to reproduce:** Add an expense using custom percentages where the calculated shares require rounding, such as $20 split as 33.33%, 33.33%, and 33.34%.

**What is wrong:** Each percentage share was rounded independently, which could make the total shares differ from the original expense amount.

**What I changed:** Calculated percentage shares in cents and assigned the remaining cents to the final participant so all shares total exactly to the expense amount.

## Bug 8

**How to reproduce:** Select Custom %, enter -10% for one participant and 110% for another, then save the expense.

**What is wrong:** The application only checked that the percentages summed to 100 and therefore accepted negative and over-100% individual percentages.

**What I changed:** Added validation requiring every percentage to be between 0 and 100 while still requiring the total to equal 100%.

## Bug 9

**How to reproduce:** Create balances where one debtor owes exactly the same amount that one creditor is owed.

**What is wrong:** When the debtor and creditor amounts were equal, the settlement algorithm advanced past both members without creating a transfer.

**What I changed:** Added the missing transfer when debtor and creditor balances are exactly equal.