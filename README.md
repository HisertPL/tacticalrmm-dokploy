# Tactical RMM on Dokploy

Dokploy deployment for Tactical RMM 1.6.1 using three public hostnames:

- `rmm.hisert.it` - dashboard
- `api-rmm.hisert.it` - REST API and agent communication
- `mesh-rmm.hisert.it` - MeshCentral

The custom Nginx configuration listens on plain HTTP port 8080. Public TLS is
terminated by the existing Cloudflare proxy/tunnel. Dokploy domain records must
therefore have HTTPS disabled and route all three hostnames to the
`tactical-nginx` service on port 8080.

The database, MongoDB, Redis, MeshCentral, and Tactical data directories use
named persistent volumes. The server-side terminal and server-side scripts are
disabled; agent terminal and agent automation remain separate Tactical RMM
features.
