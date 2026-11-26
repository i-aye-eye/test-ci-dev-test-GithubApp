# test-ci-dev-test-GithubApp

A copy of [test-ci-dev-test](https://github.com/i-aye-eye/test-ci-dev-test) for Github App (runners come from the dev GitHub App (`i-aye-eye-test-ci-dev`), not a PAT).

- No `RUNNER_ADMIN_PAT` secret, and the workflow passes none.
- A push starts a run, so its result shows on the commit. Runs started by hand (`workflow_dispatch`) work too, but GitHub doesn't show their result in the commit list or on pull requests.
- Until test-ci has `dispatch: service`, the variable `TEST_CI_DISPATCH` is set to `manual`. Each run's GH200 job then waits for a runner, which [test-ci-app](https://github.com/i-aye-eye/test-ci-app)'s `tools/app-dispatch.py` starts with the App. A run nobody gives a runner is cancelled after 24 hours.
- Without the variable, `dispatch` is `service`, and a run stops at the request job with "dispatch: service arrives with Phase B". `mvp` fails here, as there's no PAT.
