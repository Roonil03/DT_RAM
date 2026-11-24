# DT-RAM skeptical review report

Historical paper-preparation review added on 2026-11-02, associated with the snapshot recorded in the [claim–evidence matrix](claim-evidence-matrix.md) at observed repository commit `8083b49`. Findings, draft checks and environment observations below describe that review, not the current checkout. The review uses the five dimensions from the research-writing skill's adversarial review guidance; it is not a venue acceptance prediction.

For later evidence, see the [shadow pipeline audit](../analysis/shadow-pipeline-audit-2026-11-15.md), [completed Bitbrains forecasting and synthetic PPO report](../analysis/bitbrains-02-2026-11-15.md), and [evidence index](../analysis/README.md). The earlier statements about forecast dynamics and absent PPO comparisons do not describe the later implementation and synthetic evaluation. Those later experiments still do not establish live resource-management benefit.

| Dimension | Assessment | Required treatment in the paper |
|---|---|---|
| Contribution | **Needs revision / scope is narrow.** The implementation integration and trace are useful engineering evidence, but DT+RL and adjacent architecture ideas are already published. | Present as a systems integration/evidence report. Avoid algorithm novelty and efficacy claims. State what the recorded testbed did and did not exercise. |
| Writing clarity | **Pass after revision.** The draft uses one main claim per paragraph, defines the service boundary, separates observed facts from plans, and includes a pipeline figure and minimal tables. | Keep abbreviations defined and maintain “shadow”, “fidelity”, “forecast”, and “simulator” terminology consistently. |
| Experimental strength | **Needs new experiments for effectiveness claims.** One idle trace, one reported seed, shared-host measurements, no workload labels, and no policy outcomes. | Report the forecast results as preliminary. Do not claim model superiority, operational performance, or resource-management gain. |
| Evaluation completeness | **Needs new experiments.** No application metrics, heuristic/PPO comparison, ablation, workload/fault scenarios, or independent hardware evaluation. | List these as blockers to effectiveness claims and define concrete next measurements. |
| Method design soundness | **Needs revision for proposed control-loop claims.** The RL environment is simplified; forecast values do not affect simulator dynamics; safety inputs are not bound to independent/fresh evidence end to end. | Describe implemented mechanics precisely and label the predictive DT-RL control loop as incomplete. Keep actuation disabled. |

## Independent final checks

Independent Luna reviews of the draft at that stage found the implementation and forecast claims consistent with the code and stored artifacts. The formatting review reported that every citation key resolved, the conference structure and table styling were consistent with IEEEtran conventions, and source-level braces/environments were balanced. No LaTeX compiler was available during that review, so it did not include a PDF build or visual layout inspection. The author field at that stage said “DT-RAM Project Team”; replace it with the actual author names and affiliations before submission.

## Final adversarial questions

- **What new knowledge does the paper establish?** A narrow integration finding: a local k3d telemetry path and low-fidelity shadow rejection were recorded, and an idle CPU forecasting comparison was run. It does not establish control benefit.
- **Can the result be independently reproduced from this checkout?** Not fully: the processed trace and weights are absent; the handoff location is not durable. Metadata and checksums allow integrity verification if the bundle is obtained.
- **Are comparisons fair enough for the stated claim?** For the narrow forecast comparison, models use common protocol, chronological partitions, and shared score origins. The small, idle, correlated sample means the comparison is preliminary.
- **What is the most likely reviewer objection?** The paper could be viewed as an engineering progress report rather than a research contribution, especially without workload experiments or evaluated policies. The draft states this limitation and avoids claiming otherwise.
- **Are major claims supported?** Yes, when restricted to implementation artifacts, recorded k3d integration, and stored forecast metrics. Claims of improved orchestration, generalization, safety guarantees, and autonomy are unsupported and excluded.
