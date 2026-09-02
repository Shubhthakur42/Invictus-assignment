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


