# bv-deeponet-gp-ctl
Binary Voxel Deep Operator Network (BV-DeepONet) with Geometry-Physics Coupled Transfer Learning (GP-CTL) is a data-driven framework for rapid and robust structural response predictions across disparate geometric topologies. It circumvents performance oscillations triggered by non-uniform point cloud densities by transforming unstructured mesh nodes into a regularized binary occupancy tensor, ensuring density-invariant feature extraction within a 3D convolutional branch network. To overcome generalization bottlenecks under data scarcity, the GP-CTL strategy evaluates cross-domain topologies via a dual-dimensional metric of Jaccard geometric similarity and prediction uncertainty. Driven by a Four-Quadrant Hard Example Mining (4Q-HEM) mechanism, the framework dynamically prioritizes topologically complex structures and high-error anomalies to accelerate physical mapping reconstruction while anchoring baseline samples to prevent catastrophic forgetting. Tested across eighteen distinct steering wheel topologies, it secures a high validation $R^2$ score of 0.9681 and a low MAE of 0.4614. Compared to conventional full-sample training, this paradigm yields a 4.43% improvement in $R^2$ and a 27.20% reduction in MAE, while reducing the required target domain sample volume by 66.67% and accelerating training convergence by 90.00% without compromising foundational physical compliance.

Project structure:
├── 1.Data_preprocessing/           # Data regularization and feature extraction pipeline
│   ├── binary_voxelization.py      # Transform unstructured nodes into binary occupancy tensors and map coordinates
│   ├── jaccard_similarity.py       # Compute geometric similarity protocols between topologies
│   └── displacement_extract.py     # Extract target physical displacement fields from simulation
│
├── 2.Full_Sample_Baseline/         # Standard full-sample direct training implementation
│   ├── train_M_full.py             # Train the unguided baseline model (M_Full)
│   └── predict_M_full.py           # Run baseline inference and error distribution evaluation
│
└── 3.GP-CTL_Framework/             # Proposed target-aware transfer learning framework
    ├── four_quadrant_hem.py        # Execute 4Q-HEM to dynamically construct hybridized datasets via uncertainty and similarity
    ├── train_M_4q_hem.py           # Execute fine-tuning and mapping reconstruction with anchor samples
    └── predict_M_4q_hem.py         # Run accelerated cross-domain inference and contour visualization
