# claude-rename-agent

An AI-powered file renaming agent built with the Claude Agent SDK that brings
order to chaotic document folders. It reads PDFs, images, and text files,
figures out what each document actually *is*, and renames it with a clean,
consistent pattern — then remembers that pattern for next time.

## What it does

- **Analyzes documents** — extracts content from PDFs, images, and text files
  to understand their type and key metadata (date, vendor, amount, etc.)
- **Classifies documents** — identifies receipts, tax forms (W-2, 1099, K-1),
  bank statements, invoices, contracts, medical records, insurance documents,
  payslips, and more
- **Applies pattern-based naming** — uses token templates like
  `{Date:YYYY-MM-DD} - {Merchant} - {Amount}` applied consistently across a
  whole batch
- **Learns patterns** — saves a naming pattern after a successful batch run so
  the next similar folder is handled automatically
- **Batch-processes folders** — groups similar documents and renames the whole
  group in one shot with a preview-before-apply workflow

## Example usage

```bash
# Install
pip install claude-rename-agent

# Interactive session
rename-agent

# Process a folder
rename-agent --files ~/Downloads/tax-forms

# Dry run (preview only, no changes)
rename-agent --files ~/Documents/Receipts --dry-run

# Use a specific pattern
rename-agent --files ~/Downloads/bank-statements \
  --pattern "{Year}-{Date:MM} {Bank Name} Statement"
```

Or add the Claude Code skill and just ask:

```
> Rename these tax documents in ~/Downloads/tax-forms
> Organize my receipts with date and merchant name
```

## Key capabilities

| Capability | Detail |
|-----------|--------|
| Document types | 15+ types: receipts, bills, tax docs, bank statements, invoices, contracts, medical, insurance, investments, payslips, identity, correspondence, manuals, photos, general |
| Pattern tokens | `{Date}`, `{Merchant}`, `{Amount}`, `{Institution}`, `{Form Type}`, `{Account Number}`, `{Description}`, `{Title}`, and more |
| Learning | Patterns are saved per document-type and reused across sessions |
| Safety | Always previews renames before applying; `--dry-run` flag available |
| Integration | Works as a CLI tool and as a Claude Code skill |

## Requirements

- Python 3.10+
- Claude Code (for skill mode)
- `ANTHROPIC_API_KEY` environment variable

## Links

- **Repository:** https://github.com/omarshahine/claude-rename-agent
- **License:** MIT
- **Author:** [@omarshahine](https://github.com/omarshahine)
