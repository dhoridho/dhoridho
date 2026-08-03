<h1 align="center">Ridho Kurnia Putra</h1>

<p align="center">
  <b>Software Engineer</b> at PT. Akasha Wira International, Tbk.<br/>
  Backend systems &nbsp;·&nbsp; ERP platforms &nbsp;·&nbsp; Database infrastructure<br/>
  <sub>Jakarta, Indonesia</sub>
</p>

<p align="center">
  <a href="https://www.linkedin.com/in/ridhokurniaputra">
    <img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white" alt="LinkedIn"/>
  </a>
  <a href="https://dhoridho.github.io/portfolio/">
    <img src="https://img.shields.io/badge/Portfolio-09090B?style=flat-square&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSJ3aGl0ZSIgc3Ryb2tlLXdpZHRoPSIyIiBzdHJva2UtbGluZWNhcD0icm91bmQiIHN0cm9rZS1saW5lam9pbj0icm91bmQiPjxjaXJjbGUgY3g9IjEyIiBjeT0iMTIiIHI9IjEwIi8+PHBhdGggZD0iTTEyIDJhMTQuNSAxNC41IDAgMCAwIDAgMjAgMTQuNSAxNC41IDAgMCAwIDAtMjAiLz48cGF0aCBkPSJNMiAxMmgyMCIvPjwvc3ZnPg==" alt="Portfolio"/>
  </a>
  <a href="mailto:dhoridhokp@gmail.com">
    <img src="https://img.shields.io/badge/Email-14B8A6?style=flat-square&logo=gmail&logoColor=white" alt="Email"/>
  </a>
</p>

---

I work on Odoo ERP backends and the PostgreSQL infrastructure they run on. Day to day that means writing custom modules, tuning slow queries, and keeping 100+ Distribution Management System instances plus the central ERP running across several production servers.

Previously an ERP developer at HashMicro. Computer Science at Bina Nusantara University.

<br/>

## What I work on

<table>
<tr>
<td width="50%" valign="top">

**Distribution Management System**

100+ instances across several production servers. Playbooks handle backups, deploys, and health checks.

<sub>Odoo · Docker · Ansible</sub>

</td>
<td width="50%" valign="top">

**Central ERP**

Custom modules for order-to-cash, procure-to-pay, and manufacturing flows.

<sub>Odoo · PostgreSQL</sub>

</td>
</tr>
<tr>
<td width="50%" valign="top">

**Cache layer**

Caches Odoo search and read calls. With index work, cut DB CPU ~80% under peak sales force traffic.

<sub>Redis</sub>

</td>
<td width="50%" valign="top">

**Integrations**

Middleware between the ERP, external systems, and mobile apps.

<sub>REST · XML-RPC</sub>

</td>
</tr>
</table>

<br/>

## Self-initiated projects

All three are for Akasha Wira International, started from my own proposal rather than an assignment.

### Full-stack high availability for Odoo

Started as an experiment on three bare-metal servers, now approved for production rollout. The question I was chasing: can an on-premise Odoo cluster survive losing any single node, with no cloud or managed services anywhere in the design.

How each layer handles losing a node:

- **Database**: Patroni over etcd promotes a replica, PgBouncer keeps the app connected
- **Sessions**: Redis Sentinel across three nodes
- **App**: Odoo replicas on Docker Swarm behind Traefik, sticky sessions preserved
- **Filestore**: three-node MinIO quorum
- **Entrypoint**: Keepalived virtual IP
- **Visibility**: Prometheus, Grafana, Loki, Alertmanager

Verified on real hardware: any single machine can go down and the cluster keeps serving.

<br/>

### Fleet automation with Ansible

Playbooks that drive the whole instance fleet from one place: nightly database and filestore backups, rolling restarts, git pull with module upgrades, and health checks that curl every domain and only report what is actually down. Everything runs as async parallel tasks rather than one server at a time, and failures are batched into a single Discord message per server instead of flooding the channel. The Prometheus and Grafana monitoring stack deploys through the same playbooks.

Running in production across the distribution servers today.

<br/>

### RIO, a system reliability control panel in Go

When several systems integrate into one ERP, what matters is whether the records they leave behind are actually correct. RIO checks that independently of how the write happened. It runs out of band: Odoo pings it when a record is created, RIO keeps that ID on a short watch list, queries Postgres directly a few minutes later, and alerts Discord when the result is wrong, such as a self-referencing external ID or a status outside the configured whitelist. Some cases it repairs on its own. A small HTTPS dashboard shows what is currently under watch.

<br/>

## Stack

**Backend**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Odoo](https://img.shields.io/badge/Odoo-714B67?style=flat-square&logo=odoo&logoColor=white)
![Django](https://img.shields.io/badge/Django-092E20?style=flat-square&logo=django&logoColor=white)
![Go](https://img.shields.io/badge/Go-00ADD8?style=flat-square&logo=go&logoColor=white)

**Databases & Caching**

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)
![PgBouncer](https://img.shields.io/badge/PgBouncer-4169E1?style=flat-square&logo=postgresql&logoColor=white)

**Infrastructure**

![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Ansible](https://img.shields.io/badge/Ansible-EE0000?style=flat-square&logo=ansible&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white)

**AI-native workflow**

![Obsidian](https://img.shields.io/badge/Obsidian-7C3AED?style=flat-square&logo=obsidian&logoColor=white)
![Graphify](https://img.shields.io/badge/Graphify-14B8A6?style=flat-square)
![AI Agents](https://img.shields.io/badge/AI_Agents-52525B?style=flat-square)

<br/>

## Currently

- Running the Odoo ERP and distribution systems above, day to day
- Learning Go, using RIO as the practice ground
