# Metafrappe Frappe v16 port

Upstream: https://github.com/NagariaHussain/doppio/commit/51a12d65709cf9f684e558740b64dbbf5b90c51f
Deployment branch: `version-16`. App: `doppio`.

Target: Frappe 16.33.1, ERPNext 16.34.2, HRMS 16.18.1, Python 3.14,
Node 24.20.0. Shared dependencies are resolved alongside the existing 44-app bench.

Validation: disposable site install, migration, production assets, controller imports,
and focused regressions via `bench --site TEST execute doppio.tests.v16_smoke.run --kwargs '{"app":"doppio"}'`.
The validation runner installs `moto[s3,sts]` only for simulated AWS tests.
External accounts are not contacted by these regressions.

Installation in the bench catalog does not install the app on every site.
Suite and standalone Drive/Meet are alternative choices per site.
The two S3 adapters are also alternative choices per site; Improwised has its own
Python module and DocType names in this port. NextAssist requires a separately
configured `nextassist_pg` PostgreSQL connection and an AI provider on the selected site.
Suite realtime conferencing/mail features require their upstream external services.
