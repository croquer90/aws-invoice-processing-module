# Accounting Integration Notes

This module stores invoice metadata and links each validated invoice to a journal entry.

## Main Accounting Tables
- `chart_of_accounts`: defines available GL accounts
- `journal_entries`: stores the accounting header
- `journal_lines`: stores debit and credit movements

## Posting Logic
If the invoice is unpaid:
- Debit: Expense
- Credit: Accounts Payable

If the invoice is already paid:
- Debit: Expense
- Credit: Cash / Bank

The `invoices` table stores the generated `journal_entry_id` once posting is completed.
