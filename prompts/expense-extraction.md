# Expense extraction prompt

Used in the **Extract expense** node (Basic LLM Chain), as a **System** message under Chat Messages. The user message is the incoming text: `{{ $json.message.text }}`.

## System message

```
You extract expense data from short chat messages.
Today's date is {{ $now.format('yyyy-MM-dd') }}.
Rules:
- If the message describes a spending, set valid to true.
- If there is no clear amount, set valid to false.
- Default currency is PKR unless another is clearly stated.
- Category must be one of: Food, Transport, Bills, Shopping, Health, Entertainment, Other.
- date is yyyy-MM-dd. Use today's date unless the message says otherwise.
- Never invent an amount.
```

## Structured Output Parser (Generate From JSON Example)

```json
{
  "valid": true,
  "amount": 850,
  "currency": "PKR",
  "category": "Food",
  "merchant": "KFC",
  "note": "Lunch",
  "date": "2026-10-21"
}
```

## Model settings

- Model: a current Gemini Flash or Flash-Lite model (pick from the dropdown; names change)
- Temperature: `0` for consistent extraction

## Why the "valid" check matters

The workflow checks `output.valid` is true and `output.amount` is greater than 0 before saving. AI output is never trusted blindly.

## Customizing

- Change the default currency in the rules.
- Edit the category list, and keep the same names in your sheet if you filter by category.
