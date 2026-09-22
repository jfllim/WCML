# Wilbur's Portfolio

A single-page portfolio tracker. Prices, dividend history and exchange rates are
fetched live from a free public feed each time the page loads, so nothing here
needs maintaining.

## The only file you edit

**`holdings.csv`** — one line per holding. Everything else takes care of itself.

```
ticker,name,bought,price,spend,shares
TSCO.L,Tesco,2026-01-06,4.347826087,100,
AZO,AutoZone,2026-09-21,2803.25,100,
```

| Column | What to put |
| --- | --- |
| `ticker` | The market symbol. London ends in `.L` (`TSCO.L`), US is plain (`AZO`), Amsterdam `.AS`, Frankfurt `.DE`, Paris `.PA`, Zurich `.SW` |
| `name` | Whatever you want it called on the page |
| `bought` | Purchase date, `YYYY-MM-DD` |
| `price` | Price paid per share, in that market's own currency (pounds for London, dollars for the US). Leave blank to use the closing price on the purchase date |
| `spend` | The amount in pounds you put in — the share count is worked out for you |
| `shares` | A share count instead, if you'd rather state it. Leave blank if you filled in `spend` |

Fill in **either** `spend` **or** `shares`, and keep the commas between columns
even where one is empty. Lines starting with `#` are notes and are ignored.

To add a holding on GitHub: open `holdings.csv`, click the pencil icon, add your
line at the bottom, then **Commit changes**. The page shows it on the next load.

## Putting it online (GitHub Pages)

1. Create a new repository on GitHub — call it what you like, make it public.
2. Upload these three files to the root of it: `index.html`, `styles.css`,
   `holdings.csv`.
3. In the repository, go to **Settings → Pages**.
4. Under **Source** choose **Deploy from a branch**, branch **main**, folder
   **/ (root)**, and press **Save**.
5. Wait a minute, then visit `https://<your-username>.github.io/<repo-name>/`.

Bookmark that address — it's your portfolio page.

## Notes

- Reporting currency is GBP. Costs are converted at the exchange rate on the
  purchase date; current values at today's rate, so foreign holdings move with
  the pound as well as with the share price.
- London prices arrive in pence and are converted to pounds automatically.
- Dividends are the declared payments since your purchase date, on the shares
  you hold, gross of tax. They assume the position hasn't changed since.
- Prices are cached in your browser for six hours; **Refresh prices** forces a
  new fetch.
- Opening `index.html` by double-clicking it won't work — browsers block reading
  `holdings.csv` from a local file. Use the GitHub Pages address.
