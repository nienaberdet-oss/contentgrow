# contentgrow
Production-ready refresh pipeline with audit logging, RLS enforcement, alerting hooks, and CI/CD polish. Includes versioned views, smoke tests, and modular Edge Functions for scalable orchestration. Built for observability, rollback safety, and future growth.
# contentgrow

Production-ready refresh pipeline with audit logging, RLS enforcement, alerting hooks, and CI/CD polish. Includes versioned views, smoke tests, and modular Edge Functions for scalable orchestration. Built for observability, rollback safety, and future growth.

## 🔧 Features

- **Audit Logging**  
  Tracks every invocation of `send_refresh_alert` via `edge_function_audit_log`, including metadata and request path.

- **Row-Level Security (RLS)**  
  Enforced on all views and helper functions using `SECURITY INVOKER` for safe exposure.

- **Alerting Hooks**  
  Optional Slack alerts triggered when `todo_count = 0` or `failed_count > 0`, with customizable thresholds.

- **CI/CD Workflow**  
  GitHub Actions deploys migrations and invokes refresh function on tagged releases. Secrets managed via `GH_PAT`.

- **Versioned Views**  
  Materialized views like `mv_v2` support rollback and future scaling.

- **Smoke Tests**  
  Validates pipeline health using `todo_count`, `failed_count`, and audit log entries.

## 🚀 Deployment

```bash
supabase db push
supabase functions invoke send_refresh_alert --no-verify-jwt
