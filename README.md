# Flower Exchange Project

Small C++ command-line app that reads orders from a CSV file and writes execution reports to a CSV file.

## Build With Make

Run this from the project root:

```bash
make
```

Useful targets:

```bash
make        # builds exchange_app
make clean  # removes object_files/ and exchange_app
```

## Build Without Make (Optional)

```bash
g++ -std=c++17 -O2 main.cpp Exchange.cpp ExecutionReport.cpp InputValidator.cpp Order.cpp OrderBook.cpp -o exchange_app
```

## Run

```bash
./exchange_app [input_csv] [output_csv]
```

Arguments:
- `input_csv` (optional): path to the input orders file.
- `output_csv` (optional): path for the generated execution report.

Defaults when omitted:
- Input: `order.csv`
- Output: `execution_rep.csv`

## Example

```bash
./exchange_app example_orders/order2.csv execution_rep.csv
```

## Input Order Structure

Expected CSV header:

```csv
Cl. Ord.ID,Instrument,Side,Quantity,Price
```

| Column | Type | Required | Valid values / rules | Example |
|---|---|---|---|---|
| `Cl. Ord.ID` | string | Yes | Non-empty, length < 8 | `aa13` |
| `Instrument` | string | Yes | `Rose`, `Lavender`, `Lotus`, `Tulip`, `Orchid` | `Rose` |
| `Side` | integer | Yes | `1` = buy, `2` = sell | `2` |
| `Quantity` | integer | Yes | `10` to `990`, and must be a multiple of `10` | `100` |
| `Price` | decimal | Yes | Must be `> 0` | `45.00` |

