# Sample messages for testing

All amounts and merchants are made up.

## Should be saved

| Message | Expected |
|---|---|
| `Lunch 850 at KFC` | 850 PKR, Food, KFC |
| `Uber 1200 to office` | 1200 PKR, Transport, Uber |
| `Electricity bill 14500` | 14500 PKR, Bills |
| `Bought shoes for 6500 from Bata` | 6500 PKR, Shopping, Bata |
| `Pharmacy 780 medicine` | 780 PKR, Health |
| `Movie tickets 2400` | 2400 PKR, Entertainment |
| `Coffee $5` | 5 USD, Food |
| `Dinner 3200 yesterday` | 3200 PKR, Food, yesterday's date |

## Should be rejected (bot asks to retry)

| Message | Why |
|---|---|
| `bought something` | No amount |
| `hello` | Not an expense |
| `spent a lot on groceries` | No clear amount |

## Should be ignored

- Any message sent from a Telegram account other than the owner. The IF node checks the chat ID.
