---
name: bug-bounty-agents-zuma
description: >
  Motor de Seguridad Ofensiva IA para ZumaIntelligence — 43 agentes especializados
  (Bug-Bounty-Agents matty69v) + pipeline completo claude-bug-bounty (shuvonsec).
  Activar SIEMPRE con: bug bounty, pentest, recon, auditar endpoint, ssrf, idor,
  xss, sqli, api-security, nuclei, subfinder, httpx, vulnerability scan,
  auditar bgie, auditar brokerguard, auditar nucleobrokers, auditar nexus-1,
  web-hunter, bizlogic, exploit chain, validate finding, report vulnerabilidad,
  /recon, /hunt, /autopilot, /validate, /report, MATUTE ofensivo, MATUTE scan,
  security audit endpoint, test de penetración, red team, hardening endpoint.
  Consumido por MATUTE (CISO) y RUFLO ($agent-security-manager). Protocolo Verdad ON.
version: "1.0"
author: ZumaHoldingsGroup
---

# Bug-Bounty-Agents ZumaIntelligence — Motor de Seguridad Ofensiva

## Ubicaciones NEXUS-1
- Agentes prompt: ~/.claude/agents/ (260 agentes)
- Plugin completo: /root/tools/claude-bug-bounty/
- Reportes: /root/security-reports/{bgie,nucleobrokers,nexus1}
- Tools Go: ~/go/bin/{nuclei,subfinder,httpx}

## Flujo básico
claude
/recon target.com
/hunt target.com
/validate
/report

## Autopilot
/autopilot bgie-staging.tudominio.com --normal

## Workflows ZumaIntelligence

### WF-01: Audit BGIE pre-release
/recon bgie-staging.{dominio}.com
/hunt bgie-staging.{dominio}.com
# Agente bizlogic-hunter → flujos Stripe
# Agente api-security → endpoints LangGraph SSE
/validate && /report
# Output → /root/security-reports/bgie/YYYY-MM-DD.md
# MATUTE → review → Notion ticket

### WF-02: Audit NucleoBrokers-v2
/recon app.nucleobrokers.com
# idor-hunter → Supabase RLS
# auth-bypass → JWT Clerk
/secrets-hunt → verificar no hay keys en bundle
/report → PAZ para registro riesgo

### WF-03: Hardening NEXUS-1
# scope: 76.13.26.65 puertos expuestos
# Agentes: osint-investigator, asset-discoverer
# Output → MATUTE Make.com ID 4274274

## Prompt MATUTE (Make.com ID: 4274274)
Input: reporte vulnerabilidad Bug-Bounty-Agents
1. Clasificar severidad CVSS v3.1
2. Estimar impacto financiero para PAZ
3. Critical/High → alerta Telegram inmediata
4. Crear ticket Notion Security Backlog
5. Si afecta BGIE → bloquear release
Output: {severity, cvss_score, financial_impact_usd, notion_url, release_blocked}

## RUFLO ($agent-security-manager)
mcp__flow-nexus__swarm_init({topology:"hierarchical", maxAgents:4})
mcp__flow-nexus__agent_spawn({type:"researcher", role:"recon"})
mcp__flow-nexus__agent_spawn({type:"coder", role:"exploit_poc"})
mcp__flow-nexus__agent_spawn({type:"reviewer", role:"validate"})
mcp__flow-nexus__task_orchestrate({task:"audit_bgie", strategy:"parallel"})

## Reglas — Protocolo Verdad
PERMITIDO: bgie.*, nucleobrokers staging, NEXUS-1, programas H1/Bugcrowd registrados
PROHIBIDO: sistemas sin permiso escrito, produccion sin ventana mantenimiento
SIEMPRE: guardar reportes en /root/security-reports/ con timestamp
