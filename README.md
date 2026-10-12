# Canteen Chaos

The hostel canteen's ordering site. Students browse the menu, add
dishes to a cart, apply coupons, pick a collection time and place an
order. Staff watch the queue on a counter dashboard and move orders
along.

It works — mostly. Some things in it are broken, and your job is to
find and fix the ones you are given.



## Running it

```bash
cd backend
npm install
npm start
```

Open http://localhost:3000. The server serves the frontend too, so that
is the only command you need.

The canteen has opening hours (7:00 AM – 10:00 PM) and meal slots, so
outside those hours most dishes show as "not served now". If you are
working late:

```bash
TZ=Pacific/Auckland npm start
```

Other settings, all optional:

| Variable | Default | What it does |
||||
| `LATENCY_MS` | 250 | Delay added to every API call. Set `0` for instant responses. |
| `AUTO_COOK` | true | Orders move along by themselves. |
| `ORDER_RATE_MAX` | 40 | Orders per minute before you get rate limited. |



## What is in the repo

```
backend/
  server.js        wiring
  store.js         reads and writes the JSON files
  routes/          one file per resource
  logic/           where the actual thinking happens
  data/            menu, coupons, orders, ratings, members
frontend/
  index.html       three views in one page
  style.css
  js/              one module per concern
```

Two things worth knowing before you start:

- **`logic/` holds plain functions.** Pricing, validation, availability,
  the order state machine and so on. Most behaviour you can see in the
  browser is decided in there.
- **The server owns the truth.** Opening hours, stock, prices and
  discounts are all decided server-side. The browser only displays what
  it is told.

Reset the data if a test run leaves it in a strange state:

```bash
git checkout -- backend/data/
```



## Your task

You will be given a **bug log** — a list of specific problems reported
in this app. Each one describes what a person saw, not where the
problem is. Finding that is the task.

For every bug you are assigned:

1. **Reproduce it.** Make it happen on your own machine before you
   change anything.
2. **Find the cause.** The symptom and the cause are usually in
   different files.
3. **Fix it properly.** Patch the cause, not the symptom. Hiding a
   button is not the same as fixing a rule.
4. **Write it down** in `LOG.md`, in your own words:
   - what you did to reproduce it
   - what was actually wrong
   - what you changed, and why that is the right place to change it

The log matters as much as the fix. A correct patch you cannot explain
counts for nothing.



## Brownie points

Not required, and not needed to clear the task — but they count.

- **Bugs nobody reported.** There are problems in this app that are not
  in your bug log. Find one, prove it, and write it up the same way.
  Say how you noticed it.
- **A test.** A script or a check that fails before your fix and passes
  after.
- **An honest note.** Something you noticed but could not fix, or a fix
  you are unsure about, explained clearly. This scores better than
  silence.

One rule: a brownie-point fix must not break anything else. If it does,
it costs you rather than earns you.

