# website hosting and domain: what each one does, how DNS connects them, and how to run both for under $30 a year

A domain and hosting are two separate purchases that only work as a pair. The domain is the address people type into a browser; hosting is the always-on server that answers when they do. Buy one without the other and you either own an address that leads nowhere, or you have files sitting on a server nobody can find. This guide covers what each part actually does, how the two connect, where the real costs hide — renewals, mostly — and how a RackNerd setup covers both for less than what most people pay per month for managed hosting.

> **In a hurry?** RackNerd's 1GB KVM VPS at **$11.99/year** plus a .com domain (typically **$10–15/year**) puts your first year at roughly **$22–27 total** — and the promo rate renews at the same price. The catch: it's self-managed, so you need basic comfort with a server. If you'd rather never open a terminal, a managed host or a site builder is the better fit. 👉 [See RackNerd's current VPS specials and pricing](https://bit.ly/my-rn)

## Domain vs. hosting: the 60-second version

A domain is your site's address, hosting is the machine that serves the site, and DNS is the glue that connects them in a fraction of a second. When someone types your domain into a browser, DNS translates that name into your server's numerical IP address and routes the request there. Neither purchase works without the other:

|  | Domain | Hosting |
| --- | --- | --- |
| **What it is** | Your web address, e.g. `yourbrand.com` | Server space that stores your site files |
| **What it does** | Points visitors and search engines to you | Delivers your pages when someone visits |
| **If you skip it** | Your hosting has nothing memorable to connect to | Your domain leads to an error page |

That's why "I bought a domain, why isn't my website live?" is such a common complaint. Registration reserves an address through an ICANN-accredited process; it doesn't create a website. Something has to store and serve the actual files — HTML, images, code, databases — and that's the hosting side.

## Do you have to buy them from the same place?

No — DNS ties any domain to any host, so the two purchases can live anywhere. In practice there are three ways people set this up:

1. **Separate registrar and host.** Buy the domain from a dedicated registrar (GoDaddy, Namecheap, Cloudflare Registrar and Porkbun are the usual names), buy hosting elsewhere, then point DNS records at your server.
2. **Both from one provider.** One dashboard for renewals, DNS and settings. RackNerd works this way — domain registration is available in the same client area as its servers, with .com pricing in the usual $10–15/year band.
3. **A bundled platform.** Builders like Wix, Squarespace and Shopify fold hosting into the monthly subscription. A Shopify store, for instance, needs no separate hosting at all — you buy the domain and connect it.

One detail worth knowing before you pick a domain: GoDaddy's March 2025 Consumer Pulse survey found 80% of US consumers had avoided visiting or buying from a website because of an oddly spelled domain name. Clever misspellings cost you trust. Stick with .com when it's available, or a country-code extension like .co.uk if your market is mostly local.

## Where RackNerd fits in

RackNerd is a budget hosting company whose main draw is cheap KVM VPS plans with renewal prices that don't spike after year one. It's a real server — full root access, KVM virtualization, a guaranteed and isolated slice of RAM and CPU — which matters because on cheap shared hosting, one resource-hogging neighbor can slow your site down. On a KVM VPS, your allocation is yours whether or not you use it.

The practical picture:

- **KVM virtualization with full root access.** Install whatever you want: WordPress, a Node app, a mail server, three small sites on one plan.
- **Self-managed by default.** You get a SolusVM-style control panel for reinstalls, console access and reverse DNS, but patching, security and backups are your job.
- **Advertised 99.9% uptime target**, with support handled through tickets.
- **Domain registration in the same client area**, so address and server sit under one login instead of two.
- Beyond VPS, RackNerd also sells cPanel-based shared hosting for people who don't want to manage a server, and dedicated servers for heavier workloads.

The self-managed part is the whole trade-off in one sentence: you're the sysadmin, and that's why the price is a fraction of managed hosting. If that sounds like a feature rather than a chore, keep reading. If it sounds like a burden, skip to the "wrong tool" section below — no hard feelings.

## RackNerd plans and prices

The headline products are the annual KVM VPS specials, which have become something of a fixture in budget-hosting circles. Current lineup:

| Plan | RAM / vCPU | SSD storage | Monthly transfer | Price |  |
| --- | --- | --- | --- | --- | --- |
| 768MB KVM | 768 MB / 1 | 10 GB | 500 GB | **$9.99/yr** | [ Order the 768MB plan](https://bit.ly/my-rn) |
| 1024MB KVM | 1 GB / 1 | 15 GB | 1 TB | **$11.99/yr** | [ Order the 1GB plan](https://bit.ly/my-rn) |
| 2048MB KVM | 2 GB / 2 | 25 GB | 2 TB | **$19.99/yr** | [ Order the 2GB plan](https://bit.ly/my-rn) |
| 3072MB KVM | 3 GB / 2 | 40 GB | 3 TB | **$29.99/yr** | [ Order the 3GB plan](https://bit.ly/my-rn) |
| 4096MB KVM | 4 GB / 3 | 50 GB | 4 TB | **$39.99/yr** | [ Order the 4GB plan](https://bit.ly/my-rn) |

A few things the table doesn't show but should influence your order:

- **Locations.** RackNerd typically offers several US data center choices — San Jose, Los Angeles, Seattle, Dallas, Chicago, New York, Atlanta — plus Amsterdam on many deals. Availability varies per plan, so check the drop-down during checkout and pick whatever sits closest to your visitors.
- **No coupon hunting.** These special prices don't rely on promo codes; the listed rate is the rate.
- **Renewals are price-locked.** The rate you sign up at is the rate you renew at, which is the single biggest difference between RackNerd and the average "$2.99 intro offer" shared host.
- **Port speed is 1 Gbps** across the line.

For a lean blog, a portfolio, a small business site or a handful of static pages, the 1GB tier at $11.99/yr is the sweet spot. 👉 [Compare RackNerd's annual KVM plans and locations](https://bit.ly/my-rn)

## Connecting your domain to your hosting in five steps

This is the part most beginner guides skip: once you've bought a domain and a server, the site goes live when you connect them through DNS. The whole thing takes minutes of work:

1. **Find your server's IP address.** RackNerd emails it after setup, and it's visible in your VPS control panel.
2. **Open your DNS settings** — at your registrar, or at a DNS provider like Cloudflare if you'd rather route traffic through their CDN and security layer.
3. **Add an A record** pointing the root domain (`yourbrand.com`) at your server's IP, e.g. `203.0.113.10`. Add a CNAME record pointing `www` at the root domain so both addresses resolve.
4. **Issue an SSL certificate** on the server — Let's Encrypt is free — so the site loads as `https://`. The certificate has to match the domain being served, and if you move DNS later, re-issue it at the destination.
5. **Handle email separately if you need it.** MX records route mail to mail servers, and mail hosting is usually a separate product from web hosting even when it uses the same domain.

DNS changes typically propagate within minutes to a few hours. If the site doesn't load right away, don't panic and don't re-order anything; run a lookup and check whether the A record has updated first.

## What it actually costs over three years

Here's the math the "great first-year deal" marketing tends to bury. The table below compares a RackNerd path against typical market rates for shared and managed hosting:

| Setup path | Year 1 | Years 1–3 combined | Renewal behavior |
| --- | --- | --- | --- |
| RackNerd 1GB VPS + .com domain | ~$22–27 | ~$66–81 | VPS renews at signup price |
| Budget shared hosting + .com domain | ~$46–195 | varies by plan | Many hosts jump price after the intro term |
| Managed WordPress + .com domain | ~$250–495 | ~$750–1,485 | Premium from month one |

The shared and managed figures come from standard market ranges: .com domains run about $10–20/year, entry shared hosting about $3–15/month, and managed WordPress $20–40/month. Spread over three years, the gap between a self-managed VPS and managed WordPress is roughly $700–1,400.

Whether that gap is "worth it" depends entirely on you. A VPS means running your own updates, configuring backups and reading the occasional error log. Plenty of people are happy to do that for a site that costs less per year than a single month of managed hosting. Plenty of others would pay the premium to never think about it. Both are correct answers. 👉 [Check RackNerd's current rates and lock in a plan](https://bit.ly/my-rn)

## When RackNerd is the wrong tool

Honesty section, because recommending a $12/year server to everyone would just create refund requests:

- **You want one-click everything.** If updates, backups and security patches should be somebody else's problem, managed WordPress hosting exists precisely for that — at $20–40/month.
- **You want a drag-and-drop builder.** Wix or Squarespace handle hosting, templates and editing in one subscription. No server, no terminal.
- **You're selling on Shopify.** Hosting is already included; the only purchase is the domain, which you connect to the store.
- **You've never administered a server and don't want to learn.** Even with a free control panel installed, a VPS occasionally requires Googling error messages at midnight.

If none of those apply — or you actively enjoy having root access — the VPS math is hard to argue with.

## FAQ

**Can I buy the domain now and hosting later?**
Yes. A registered domain sits parked until DNS records point it somewhere. You can secure the name months before launch — just review the auto-renew setting so it doesn't lapse unnoticed.

**Do you ever own a domain outright?**
No. Registration is a lease, billed yearly. Stop renewing and the domain eventually enters a redemption period, after which anyone can register it. This is why price-locked hosting paired with a domain you actually renew is the setup that survives long term.

**Is a $10–12/year VPS genuinely usable?**
For small sites, yes. 1GB of RAM with dedicated, isolated resources runs a lean WordPress install or a static site comfortably, and KVM isolation means noisy neighbors can't throttle you. Where it stops being enough: a busy WooCommerce store. Store owners are consistently advised not to skimp on speed, because every second of load time costs sales.

**Do I need separate email hosting?**
Usually, yes. MX records are configured independently of your website's A records, and most providers bill mail hosting as its own product even when addresses match your domain.

**Should hosting and domain be bought from the same company?**
It's a convenience question, not a technical one. DNS connects any registrar to any host. One dashboard just means fewer passwords and fewer renewal emails to track.

## Picking by situation

- **Personal site, blog, portfolio, small business page, and you can follow a copy-paste tutorial** → RackNerd's 1GB KVM at $11.99/yr plus a $10–15 .com. Total first year: around $25.
- **Running WooCommerce as a real store and never want to see a server** → managed WordPress instead; speed and support justify the monthly fee.
- **Selling on Shopify** → skip hosting entirely, buy the domain and connect it to the store.
- **Expecting big traffic spikes or running an app** → a higher-tier VPS or cloud hosting with room to scale.

One last check before ordering: confirm your preferred data center location is in stock for the plan you want, and set a calendar reminder for the domain renewal date regardless of who you register it with. Then 👉 [order your RackNerd VPS and domain in one client area](https://bit.ly/my-rn) and you'll have both halves of the setup — address and server — before the coffee gets cold.
