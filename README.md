# WheelOS Prediction

Independent `wheelos_prediction` capability module containing `prediction`.

The source layout, C++ includes and Proto import paths retain `modules/...`.
Components and tests remain individually selectable; sharing a package does
not merge runtime processes or require every GPU model to be built.

Use the mapped non-root managed container. From this checkout, run
`bazelisk cquery --config=dev -c opt //modules/prediction:libprediction_component.so`; the Apollo product uses
`@wheelos_prediction//modules/...` through opt-in development overrides.
Live vehicle/map/model selection belongs to deployment configuration.

SDK installs apply `third_party/rules_pkg/execroot_runfiles.patch`.
Consuming roots must carry that override; dependency-root overrides do not apply.
This ignored checkout must accompany product changes. Its Git source is
registered in `wheelos.repos`; no Bzlmod registry release has been published.

Configured CPU analysis is not GPU inference acceptance. GPU targets
retain their CUDA/TensorRT/model requirements; broad unconfigured
queries may load disabled or legacy backend repositories.
