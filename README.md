<div align="center">

<!-- ── HEADER ── -->
<img src="https://capsule-render.vercel.app/api?type=venom&color=0:0d1117,50:1a7f37,100:2ea043&height=200&text=vishwam&fontSize=64&fontColor=e6edf3&animation=fadeIn&desc=backend%20engineer%20%C2%B7%20i%20break%20systems%20on%20purpose%20to%20learn%20what%20they%20guarantee&descSize=15&descAlignY=70" width="100%"/>

<!-- ── TYPING ── -->
<a href="https://github.com/Vishwam401/relay">
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=500&size=20&pause=1200&color=2EA043&center=true&vCenter=true&width=640&lines=building+relay+%E2%80%94+a+durable+job+engine+from+Postgres+primitives;kill+-9+the+worker.+the+job+must+survive.;every+dependency+earns+its+place+or+stays+out;exactly-once+side+effects%2C+even+after+5+crashes" alt="typing" />
</a>

<br/><br/>

<img src="https://komarev.com/ghpvc/?username=Vishwam401&style=flat-square&color=2ea043&label=profile+views" alt="profile views"/>
&nbsp;
<a href="https://github.com/Vishwam401?tab=followers"><img src="https://img.shields.io/github/followers/Vishwam401?style=flat-square&color=2ea043&labelColor=0d1117&label=followers" alt="followers"/></a>
&nbsp;
<a href="https://leetcode.com/Vishwam1708"><img src="https://img.shields.io/badge/leetcode-Vishwam1708-ffa116?style=flat-square&labelColor=0d1117&logo=leetcode&logoColor=ffa116" alt="leetcode"/></a>

</div>

<br/>

```console
$ relay status --engineer vishwam

  STATE      running
  UPTIME     shipping since 2024
  QUEUE      [1] relay: durable job engine      ← executing
             [2] llm execution layer             pending (month 2)
             [3] scale ceiling measurement       pending (month 4)
  RETRIES    unlimited. backoff: none.
  DLQ        empty — failures get postmortems, not silence
```

---

## 🧑‍💻 About me

<div align="center">
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=500&size=17&pause=1500&color=2EA043&center=true&vCenter=true&width=640&lines=SELECT+*+FROM+engineers+WHERE+username+%3D+'Vishwam401'%3B;i+build+on+Postgres+primitives+%E2%80%94+so+here's+my+row+%E2%86%93" alt="about query" />
</div>

```sql
relay=# SELECT * FROM engineers WHERE username = 'Vishwam401';

-[ RECORD 1 ]----+---------------------------------------------------------------
name             | Vishwam
location         | India 🇮🇳
role             | backend engineer
isolation_level  | SERIALIZABLE          -- one thing at a time, done properly
thesis           | "Using a queue teaches you its API.
                 |  Building one teaches you its guarantees."
portfolio_shape  | wide  → alpha-commerce (40+ endpoints, proves range)
                 | deep  → relay (one system, proves judgment)
strong_at        | {async APIs (FastAPI + asyncpg),
                 |  Postgres internals — MVCC · isolation · row locks,
                 |  payments & webhook security (Razorpay, HMAC-SHA256),
                 |  auth engineering (JWT rotation, Argon2, rate limits),
                 |  background jobs (Celery + RabbitMQ — rebuilding from scratch)}
debug_strategy   | print() first, debugger later 🤫
deadlocks        | 0                     -- I always acquire locks in the same order
last_vacuum      | never                 -- no dead tuples in this career
status           | active ⚡

(1 row)
```

---

## ⚙ What I'm building

<div align="center">
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=500&size=18&pause=1300&color=2EA043&center=true&vCenter=true&width=680&lines=two+projects.+one+proves+range%2C+one+proves+judgment.;relay+%E2%80%94+no+Redis.+no+broker.+just+Postgres+%2B+discipline.;alpha-commerce+%E2%80%94+40%2B+endpoints%2C+live+in+production;kill+the+worker.+the+job+survives.+that's+the+whole+point." alt="projects typing" />
</div>

<br/>

### [relay](https://github.com/Vishwam401/relay) — a durable job execution engine, from Postgres primitives

**The contract (this *is* the product):**

| # | Guarantee | Mechanism |
|---|---|---|
| 1 | An accepted job is never lost | commit-before-202, single source of truth |
| 2 | Side effects happen exactly once — even if the worker crashes 5 times | idempotency keys + unique constraints |
| 3 | Failures retry with bounds, not forever | exponential backoff + jitter |
| 4 | Dead jobs go to a DLQ, never silently vanish | max-attempts → dead letter |
| 5 | You can always ask where a job is | `GET /jobs/{id}` |

No Redis. No RabbitMQ. No broker. Just PostgreSQL, `FOR UPDATE SKIP LOCKED`, leases, and a reaper. Every non-obvious choice lands in `DECISIONS.md` as *problem → options → chose → **cost** → rejected because*. If I can't write the cost, I didn't understand the decision.

### [alpha-commerce](https://github.com/Vishwam401/E-commerce) — production-grade e-commerce backend

<div align="center">

<a href="https://www.alpha-commerce.tech/">
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=18&pause=1000&color=2EA043&center=true&vCenter=true&width=560&lines=%24+curl+-I+https%3A%2F%2Falpha-commerce.tech;HTTP%2F2+200+%E2%80%94+deployed.+not+a+localhost+project.;40%2B+endpoints+%C2%B7+payments+%C2%B7+auth+%C2%B7+real+traffic" alt="alpha-commerce live" />
</a>

<br/>

<a href="https://alpha-commerce.tech">
  <img src="https://img.shields.io/badge/⚡_visit-alpha--commerce.tech-2ea043?style=for-the-badge&logo=googlechrome&logoColor=white&labelColor=0d1117" alt="visit alpha-commerce.tech"/>
</a>
&nbsp;
<a href="https://github.com/Vishwam401/E-commerce">
  <img src="https://img.shields.io/badge/source-E--commerce-c9d1d9?style=for-the-badge&logo=github&logoColor=white&labelColor=0d1117" alt="source code"/>
</a>

</div>

**Key engineering decisions:**
- Dual-token JWT with refresh rotation, theft detection & Redis blacklist
- Atomic stock management with row-level locking
- HMAC-SHA256 webhook verification for Razorpay
- Coupon engine with per-user tracking & race-condition safety
- Celery async invoice delivery with auto-retry · Docker-first, Alembic migrations

---

## 🔬 Things I broke on purpose (and measured)

I don't collect tools — I collect failure modes. Every claim below is measured, not read about:

| Experiment | What actually happened |
|---|---|
| `time.sleep` inside an async endpoint, 3 concurrent requests | **6.04s** vs **2.04s** with `asyncio.sleep` — one blocking call serialized the whole event loop |
| `kill -9` a worker mid-job | No cleanup ran. Job stuck in `running` forever. This single failure is why leases + reapers exist |
| `docker stop` vs `docker kill` on PID 1 | Without a handler, PID 1 never even *receives* SIGTERM — 10s grace, then exit `137` |
| Two transactions, one row, Read Committed | Lost update, **silently** — got `101`, correct answer was `102`. No error. Nothing |
| Write skew: two txns both check a constraint, both pass | Constraint broken anyway. `REPEATABLE READ` doesn't stop it. `SERIALIZABLE` does — by throwing `40001` at you |
| Connection pool capped at 2, 10 concurrent requests | Looks exactly like "the DB is slow." The DB was fine. The queue-wait hides inside your latency |
| Connect timeout vs read timeout | `connect` fail = request never arrived → retry is safe. `read` fail = **unknowable** → retry may double a side effect |

These aren't bugs I hit — they're bugs I *scheduled*. The failure matrix is the syllabus.

---

## 🧰 Stack

<div align="center">

**languages**
<br/>
<img src="https://skillicons.dev/icons?i=python,cpp&theme=dark" alt="python, c++"/>

**backend**
<br/>
<img src="https://skillicons.dev/icons?i=fastapi,nodejs,graphql&theme=dark" alt="fastapi, nodejs, graphql"/>

**data**
<br/>
<img src="https://skillicons.dev/icons?i=postgres,redis,mongodb&theme=dark" alt="postgres, redis, mongodb"/>

**infra & tools**
<br/>
<img src="https://skillicons.dev/icons?i=docker,rabbitmq,linux,git,github,githubactions&theme=dark" alt="docker, rabbitmq, linux, git, github, actions"/>

</div>

```text
orm/migrations   sqlalchemy 2.0 · alembic · pydantic
testing          pytest · hypothesis — "after any crash sequence, side-effect count == 1"
reading          designing data-intensive applications · kurose ch.3 · production postmortems
```

---

## 📐 How I learn

```
for every dependency:
    what does it guarantee — and what does it NOT?
    if it dies, does my system degrade or die with it?
    what happens if this work executes twice?
    if state lives in two places, who keeps them honest?
    under load, what breaks first?
```

- **Weekly postmortem ritual** — reading other people's incidents (Cloudflare, Buttondown, incident.io) as a substitute for on-call scars
- **Plan and log are never the same file** — the plan states intent, the log states measured outcome
- **Measured vs inferred** — every claim in my logs is labeled. "Likely" is not "confirmed"

---

## 📊 Numbers

<div align="center">

<img height="180" src="https://github-profile-summary-cards.vercel.app/api/cards/stats?username=Vishwam401&theme=github_dark" alt="GitHub stats"/>
&nbsp;
<img height="180" src="https://github-profile-summary-cards.vercel.app/api/cards/most-commit-language?username=Vishwam401&theme=github_dark" alt="Top languages by commit"/>

<br/><br/>

<img src="https://streak-stats.demolab.com?user=Vishwam401&hide_border=true&background=0d1117&ring=2ea043&fire=ffa116&currStreakLabel=2ea043&sideLabels=c9d1d9&sideNums=e6edf3&currStreakNum=e6edf3&dates=8b949e" alt="GitHub streak"/>

<br/><br/>

<a href="https://leetcode.com/u/Vishwam1708/">
  <img src="https://leetcard.jacoblin.cool/Vishwam1708?theme=dark&font=JetBrains%20Mono&ext=heatmap&border=0&radius=12" alt="LeetCode stats"/>
</a>

</div>

---

## 🌌 Contribution topology

<div align="center">

<!-- 3D contribution graph (generated by your profile-3d-contrib workflow — verify the exact SVG filename in that folder) -->
<img src="./profile-3d-contrib/profile-night-rainbow.svg" alt="3D contribution graph" width="100%"/>

<!-- Snake (generated by snake.yml — paths from your previous README's output branch) -->
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Vishwam401/Vishwam401/output/github-snake-dark.svg"/>
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/Vishwam401/Vishwam401/output/github-snake.svg"/>
  <img alt="Contribution snake" src="https://raw.githubusercontent.com/Vishwam401/Vishwam401/output/github-snake-dark.svg" width="100%"/>
</picture>

<br/><br/>

<img src="https://github-readme-activity-graph.vercel.app/graph?username=Vishwam401&bg_color=0d1117&color=c9d1d9&line=2ea043&point=ffa116&area=true&hide_border=true" alt="Activity graph" width="100%"/>

</div>

---

## 📬 Let's connect

<div align="center">

```console
$ relay enqueue --type "collaboration" --payload "your idea here"
→ 202 Accepted  { "status": "pending", "response_sla": "fast" }
```

<a href="mailto:vishwam.connects@gmail.com">
  <img src="https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email"/>
</a>
&nbsp;
<a href="https://www.linkedin.com/in/vishwam-vaghasiya/">
  <img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"/>
</a>
&nbsp;
<a href="https://leetcode.com/u/Vishwam1708/">
  <img src="https://img.shields.io/badge/LeetCode-FFA116?style=for-the-badge&logo=leetcode&logoColor=black" alt="LeetCode"/>
</a>
&nbsp;
<a href="https://github.com/Vishwam401/relay">
  <img src="https://img.shields.io/badge/relay_→-181717?style=for-the-badge&logo=github&logoColor=white" alt="relay"/>
</a>

<br/><br/>

<img src="https://capsule-render.vercel.app/api?type=venom&color=0:2ea043,100:0d1117&height=100&section=footer" width="100%"/>

</div>
