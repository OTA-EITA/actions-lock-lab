# actions-lock-lab

Experiments with GitHub Actions workflow lockfiles (`actions.lock`), run on 2026-10-31 with `gh actions-lock` v0.4.0. The action under test is [OTA-EITA/actions-lock-lab-action](https://github.com/OTA-EITA/actions-lock-lab-action), whose `v1` and `v2` tags were force-pushed on purpose.

| # | Case | Commit that ran | Run |
|---|---|---|---|
| E2 | `v1` force-pushed to a descendant commit, locked workflow | locked commit | [41189812211](https://github.com/OTA-EITA/actions-lock-lab/actions/runs/41189812211) |
| E9 | `v1` force-pushed to an unrelated history | none, the run failed | [41190293617](https://github.com/OTA-EITA/actions-lock-lab/actions/runs/41190293617) |
| E3 | new workflow not in the lockfile | the moved tag | [41189858310](https://github.com/OTA-EITA/actions-lock-lab/actions/runs/41189858310) |
| E8 | cross-repository reusable workflow (`jobs.<id>.uses`) | the moved tag | [41190242291](https://github.com/OTA-EITA/actions-lock-lab/actions/runs/41190242291) |
| E7 | `gh actions-lock --relock` after the tag moved | warns `ref-moved`, then pins the moved commit, exit 0 | [41189978202](https://github.com/OTA-EITA/actions-lock-lab/actions/runs/41189978202) |

The workflows here are deliberately in odd states (for example `use-action.yml` and the lockfile do not always agree). Do not copy them as they are.
