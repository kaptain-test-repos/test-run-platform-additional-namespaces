# Test Run Platform Additional Namespaces

E2E test repo for the `kubernetes-run-platform-meta-environment` build in
buildon-github-actions.

Tests the RP-only additionalNamespaces oversight feature (plan section 12,
design to be discussed before implementing): whitelist-based watching of
namespaces the RP does not manage - strict mode on `default` (nothing
permitted), a kube-system allowlist mixing exact names, name patterns, and
label selectors, and a per-namespace `cleanUpPolicy: enabled` override on
kube-public while the top-level master stays dryrun. Additional namespaces
never ADD anything - they only remove or alert on the unexpected.

Child: `test-run-env-deployment-keel-all-in-one` (one env, kept minimal so
the additional-namespaces behaviour is the only variable).

Pending notes:

- Section 12 is discuss-before-implement; this repo pins down the intended
  config surface so the discussion has a concrete fixture.
- The draft `spec-kaptainpm-schema` must be faked into the build before this
  repo can build.
- Behaviour assertions get added to the hooks once the reference scripts land.
