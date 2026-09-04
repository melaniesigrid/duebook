# Duebook — working agreement

## Spending rule — before anything else

**No agent commits more than US$10 of vendor spend without asking Melanie first.**

This outranks finishing the task. An agent that stops at $10 and reports has done
the right thing; an agent that finishes the job and presents a bill has not,
however good the work is.

**What counts.** Anything metered by a third party with a card behind it —
Google Places/Maps, Anthropic, OpenAI, Gemini, Resend, Neon compute, Vercel
overages, ad spend, storage, build minutes.

**What to do.**

1. **Price the worst case out loud, before the first call.** Before any batch,
   backfill, bulk scoring run, eval sweep, or anything that loops over a corpus
   calling a vendor: compute `requests x unit price` using the vendor's real
   current per-SKU price — look it up, do not recall it — and state the number.
2. **If the worst case is over $10, stop and ask.** Say what you are doing, what
   it costs, and what it buys. Wait for a yes. Do not resume on your own
   judgment, and do not split the work into smaller runs to stay under the line.
3. **Never raise a cap, disable a guard, or route around a ledger to get
   unblocked.** Being blocked by a spend cap is the cap working.
4. **A new metered vendor needs a meter before its first call.** A vendor nothing
   meters is a vendor nothing caps.

**Four things that are not optional.**

- **The ceiling goes in before the loop does.** Anything calling a paid API more
  than once needs a hard maximum and a stop condition, written before the first
  run.
- **Cap the total, not the per-user share.** A per-user quota is not a bill: the
  bill is the sum over every user, and in development "every user" means every
  seed account, every dev auth seam, and every agent session that made one.
- **A cap in the code is not a cap.** The provider's own console needs a budget
  alert and a hard quota too. An application limit cannot survive a bug in the
  application, which is precisely when it is needed.
- **Kill a runaway before diagnosing it.** A retry storm, a loop that will not
  terminate, a hung job — stop it first, then investigate.

**Why, with the receipt.** Between 2026-08-24 and 2026-08-28 ZipQuarry billed
**US$671.66** of Google Places — 19,190 Text Search requests at the Enterprise
rate of $35/1,000 — on a $758.98 invoice, against a pre-revenue product with zero
customers and zero revenue. The meter was written four days after billing
started; a pagination loop billed a request every 300ms until it was killed by
hand; no console budget existed; the per-user quota was 400 requests/day, which
is $42/day across three dev accounts all comfortably inside their limits; and the
$200/month Google credit everyone was mentally budgeting against no longer exists
(it is per-SKU monthly free tiers now, and Text Search Enterprise gets 1,000
calls a month). Postmortem: `zipquarry-platform/docs/SPEND-INCIDENT-2026-08.md`.
