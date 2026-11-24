# Research Paper: Results & Discussion

Historical summary of the preliminary k3d CPU forecasting comparison. This study did not include an ablation study or decision regret analysis; later offline experiments are listed in the [evidence index](../analysis/README.md).

## Forecasting evaluation on recorded k3d telemetry

Seven forecasting approaches were evaluated on 5,004 telemetry events labeled
with three k3d node IDs. CPU and memory measurements were host-scoped, so the
capture does not represent three independent physical nodes. The comparison
used chronological 60/20/20 partitions and 5, 10,
30, and 60 second horizons. Missing one-second buckets were not imputed. The
documented 60-sample history yielded no valid windows, so the comparison used
a 20-sample history and records this deviation explicitly.

The temporal convolution had the lowest mean validation RMSE (0.013083), a
5,021-byte artifact, and 0.069 ms mean test inference latency. Its 200-repeat
direct-inference p95 was 0.180 ms and its in-process API p95 was 16.199 ms on
the 16-logical-CPU Windows testbed host. GRU had the lowest mean test RMSE
(0.016219), but it was not selected from test results.

No model is recommended for activation. The capture contains only an idle
baseline, k3d nodes share one host, target-edge live-network latency was not
measured, and only three correlated per-node calibration residuals were
available per horizon. The evaluator therefore reports interval coverage as
unavailable rather than assigning a nominal 90% label. The model is suitable
only for further shadow evaluation on a longer, labeled workload and fault
trace. Full tables, metadata, and plots are in
[`experiments/analysis/k3d-20261101-forecasting`](../../experiments/analysis/k3d-20261101-forecasting/README.md).
