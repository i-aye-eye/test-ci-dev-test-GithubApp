# test-ci-dev-test-GithubApp

A copy of [test-ci-dev-test](https://github.com/i-aye-eye/test-ci-dev-test) for Phase B2: runners come from the dev GitHub App (`i-aye-eye-test-ci-dev`), not a PAT.

- No `RUNNER_ADMIN_PAT` secret, and the workflow passes none.
- Not registered with ci-service yet. In B2 it's registered through the App, by name.
- CI runs only when started by hand (`workflow_dispatch`), until test-ci has `dispatch: service`. Until then a run stops at the request job with "dispatch: service arrives with Phase B".
- Set `TEST_CI_DISPATCH` to `mvp` or `manual` to override, as in test-ci-dev-test; `mvp` fails here without the PAT.
