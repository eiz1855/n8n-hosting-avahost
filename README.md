# n8n hosting: How Much RAM Do You Need, Is PostgreSQL Included, and What Does AvaHost's €5 Plan Cover? (Plan Table and Setup Notes)

AvaHost's n8n hosting is a one-click self-hosted stack priced from **€5** for the n8n application and PostgreSQL database. It includes automatic n8n updates, scheduled backups, custom-domain support, and automated HTTPS. AvaHost describes the mapped plan as suitable for "a small number of light workflows," which is the right starting point for a solo operator or a small team running a handful of automations.

Two things need checking before you pay. AvaHost's n8n page does not publish CPU, RAM, or storage for that plan, and it does not state the billing period or renewal price for the €5 figure. The PostgreSQL database is included but remains unmanaged by AvaHost. Those gaps do not make the plan a bad buy, but they change what you should confirm before choosing it over a VPS or a managed n8n service.

> **Quick take:** AvaHost's Plan 2 is the entry point for n8n, priced at **€5** for the application and PostgreSQL stack. It suits a small number of light workflows, with updates, backups, a custom domain, and HTTPS included. Confirm the RAM/CPU allocation, billing period, renewal price, and database management terms before ordering.
>
> 👉 [See AvaHost's n8n plan](https://my.ava.hosting/aff.php?aff=15562)

## AvaHost n8n hosting plans and published details

AvaHost's n8n page maps the app to Plan 2. Its app catalog lists n8n "From €5," which matches that entry point. No second n8n-specific tier is shown on those pages, so the table below covers the published n8n plan rather than a multi-tier lineup.

| Plan | Published configuration | Price and billing | Best for | Order |
| --- | --- | --- | --- | --- |
| **Plan 2 (n8n mapping)** | One-click n8n and PostgreSQL; official n8n Docker image on the latest tag; default port 5678; automatic n8n updates; scheduled backups; custom domain; automated HTTPS; PostgreSQL unmanaged | **€5**; billing period and renewal price not published | A small number of light workflows; a single n8n instance that needs a real PostgreSQL database | [See the AvaHost n8n plan](https://my.ava.hosting/aff.php?aff=15562) |

A second set of details matters just as much as the price:

| Detail | What AvaHost publishes |
| --- | --- |
| Provisioning | One-click deployment provisions n8n and PostgreSQL, then connects them automatically |
| Database | PostgreSQL is included but remains unmanaged by AvaHost |
| Updates | AvaHost applies n8n updates automatically while persistent application data and PostgreSQL remain attached |
| Backups | Scheduled backups are included |
| Domain and HTTPS | Custom-domain support and automated HTTPS are included |
| Default port | 5678 |
| CPU, RAM, storage | Not published on the n8n page |
| Billing period, renewal, refund, region | Not published on the n8n page |
| Queue mode | Not mentioned on the n8n page |

AvaHost says busy webhook endpoints, large files, or concurrent long-running workflows may require a larger plan. That is the practical escape hatch if Plan 2 turns out to be too small. Ask for the next tier's CPU, RAM, and storage before you need it, because the n8n page does not lay out an upgrade table.

## What "pre-installed" means at AvaHost

"Pre-installed" covers several different levels of setup. AvaHost sits closer to the done-for-you end than a bare VPS: you get n8n, PostgreSQL, automatic updates, backups, a custom domain, and HTTPS without assembling the stack yourself. The database is connected for you, but it stays unmanaged, so database administration and recovery planning are still your responsibility.

Other hosts show how wide that spectrum is. IONOS' VPS+ puts n8n, Docker, and the Web UI on the server, then you open port 5678 and log in. Its dedicated servers add a Let's Encrypt certificate. One.com preconfigures Docker and PostgreSQL and advertises a zero-command-line setup with root access. Hostinger ships an "Ubuntu 24.04 with n8n" template, a separate queue-mode template, and a template with more than 100 pre-made workflows. The official Hetzner guide is the manual end: Caddy as a reverse proxy, Docker Compose, SQLite by default, a DNS A record, and ports 80 and 443 opened in the firewall.

For a small n8n deployment, AvaHost's combination is useful because PostgreSQL is the right database for production and the update and backup chores are handled. The missing pieces are published resource limits and a queue-mode option. If either matters to your workload, get an answer before you order.

## How much RAM and CPU does n8n need?

n8n can run on modest hardware, but the optional n8n Assistant raises the floor. n8n's deployment documentation says the Assistant's sandbox runner uses Docker-in-Docker and needs at least **4 GB RAM and 2 vCPU**. That runner must stay on the internal network, with no published ports and no reverse proxy route pointing at it.

If you plan to use the Assistant, treat 4 GB RAM and 2 vCPU as the minimum and ask AvaHost whether Plan 2 meets it. If you only run a few webhook and schedule workflows without the Assistant, a smaller instance can work, but 2 GB is not a safe default once PostgreSQL, retained execution history, and occasional large payloads are in the picture. AvaHost's n8n page does not publish the allocation, so this is a question for support rather than a number you can read off the plan.

Queue mode is a separate decision. It spreads workflow executions across multiple workers and is useful when webhooks arrive in bursts or workflows run long. AvaHost's n8n page does not advertise queue mode. If you expect multiple workers, ask before buying. A €5 instance described for light workflows is not a queue-mode cluster.

👉 [Open AvaHost's n8n plan page](https://my.ava.hosting/aff.php?aff=15562)

## PostgreSQL is included, but it is unmanaged

n8n's own default is SQLite when queue mode is off. SQLite is fine for development and small single-instance setups. Production deployments should use PostgreSQL. MySQL and MariaDB are not supported, and n8n does not test or certify PostgreSQL-compatible forks, so a "PostgreSQL-compatible" database is not the same as a supported one.

AvaHost's choice of PostgreSQL is the right default for a hosted n8n stack. The caveat is management. AvaHost provisions and connects the database, but it remains unmanaged. Scheduled backups are included, yet you should know how restores work and test one before a workflow becomes business-critical. AvaHost also applies n8n updates automatically, so workflow owners should review release notes after major updates and test automations that depend on changed nodes or credentials.

This is a better starting point than a template that leaves you on SQLite and expects you to migrate later. It is not a fully managed database service, and the page does not pretend otherwise.

👉 [Start with the AvaHost n8n and PostgreSQL plan](https://my.ava.hosting/aff.php?aff=15562)

## The real cost of a €5 n8n plan

A headline price is only useful once you know the term and the renewal. Hostinger's KVM 1 is a useful example of how the advertised monthly figure works: **$6.49/mo** is the 24-month prepaid rate, you pay **$155.76** today, and it renews at **$11.99/mo** for the same term. The renewal is about 85% higher than the promotional rate, and the next 24 months cost **$287.76**. A reader who compares only the $6.49 figure will underestimate the second term.

One.com uses the other model: a one-month contract, monthly billing, a 15-day notice period, and a £0 setup fee, with five cloud-server sizes from 2 vCPU and 4 GB RAM up to 16 vCPU and 32 GB RAM. IONOS' dedicated n8n servers are priced as a fixed monthly fee regardless of workflow volume. One.com and IONOS did not publish prices on the pages available for this comparison, so their specifications and contract terms can be compared, but their total costs cannot.

AvaHost's €5 is the entry price for the application and PostgreSQL stack. The n8n page does not say whether that is monthly, annual, or a promotional starting rate. Ask for the billing period, renewal price, and refund window before you pay. A low entry price with an unknown renewal is not a total cost.

👉 [Check AvaHost's €5 n8n plan before comparing total costs](https://my.ava.hosting/aff.php?aff=15562)

## Who should not choose AvaHost for n8n

AvaHost's n8n plan fits a solo operator or small team with a handful of workflows, a need for PostgreSQL, and a willingness to own workflow logic. It is a poor fit in several common situations.

- **You need queue mode or many concurrent executions.** AvaHost does not advertise a queue-mode template, and the €5 plan is described for light workflows. Ask for a larger plan and confirm worker support before you commit.
- **You want someone else to troubleshoot n8n workflows.** Hostinger explicitly limits its support to the VPS environment and excludes workflow configuration and custom code. One.com calls its VPS unmanaged and says n8n updates are your job. AvaHost automates n8n updates and backups, but its database is unmanaged and its n8n support scope is not described on the page.
- **You need a published data region or refund window before paying.** AvaHost's n8n page does not list either. If data residency or a trial period is a condition of purchase, get it confirmed first.
- **You plan to run local AI models.** A €5 app plan described for light workflows is not a local-inference server. IONOS' dedicated n8n servers are the type of product that supports local models such as Llama, and even there you need to size the machine for the model.
- **Prebuilt connector count is your deciding factor.** Hostinger's own comparison puts n8n at around 1,900 connectors versus more than 5,000 for Zapier. Check your must-have apps before migrating.

## n8n hosting FAQ: MySQL, RAM, queue mode, and first login

**Can I use MySQL or MariaDB with n8n?**
No. n8n supports SQLite and PostgreSQL. MySQL and MariaDB are not supported. AvaHost uses PostgreSQL, which is the right choice for production.

**Is 2 GB RAM enough for n8n?**
For a light single-instance setup without the Assistant, it can be, but it leaves little headroom for PostgreSQL, execution history, and large payloads. If you plan to use the n8n Assistant, the sandbox needs at least 4 GB RAM and 2 vCPU. AvaHost does not publish Plan 2's allocation, so ask.

**Do I need queue mode?**
Only if you need to spread executions across multiple workers, for example when webhooks arrive in bursts or workflows run long. A small team running a few scheduled jobs does not need it. AvaHost does not mention queue mode on its n8n page.

**What login will I get on first access?**
AvaHost's page does not describe the first-login flow. On some prebuilt n8n VPS stacks, the web UI is protected by HTTP Basic Auth with the username `admin` and the server's root password. Check the onboarding email rather than assuming those credentials.

**Does AvaHost charge extra for n8n?**
AvaHost prices n8n as part of the Plan 2 application and PostgreSQL stack. External API subscriptions and usage charges are separate. There is no separate n8n licence line on the page.

**Can I use my own domain and HTTPS?**
Yes. Custom-domain support and automated HTTPS are included with the n8n plan.

**Is the PostgreSQL database managed?**
No. It is provisioned and connected automatically, but AvaHost leaves it unmanaged. Scheduled backups are included, so ask how restores are handled.

**Is there a trial or refund period?**
The n8n page does not state one. Confirm the refund policy before paying.

## Before you order

Pick **Plan 2 at €5** if you have a small number of light workflows and want n8n, PostgreSQL, automatic updates, backups, a custom domain, and HTTPS without building the stack yourself. Ask for a larger plan if you need queue mode, many concurrent webhooks, large payloads, or local AI. Those requirements sit outside what the €5 mapping is described to handle.

Before paying, get four things confirmed: the billing period and renewal price, the CPU/RAM/storage allocation, whether queue mode is available, and the refund or trial terms plus the data region. If those answers match your workload, AvaHost's one-click stack is a low-friction way to get a self-hosted n8n instance running with a real database. If you need someone else to own workflow troubleshooting, a managed service is the better fit.

👉 [Open AvaHost's n8n plan page](https://my.ava.hosting/aff.php?aff=15562)
