# ICLR 2023 Multimodal Representation Learning Workshop Summary
Summary of the ICLR 2023 Multimodal Representation Learning Workshop


## Worshops covered

- A Picture is Worth a Thousand Words: Language Models Plan from Pixels [Paper](https://openreview.net/pdf?id=3hTpRkGohE)
- Multimodal Subtask Graph Generation from Instructional Videos [Paper](https://openreview.net/pdf?id=zJhWyDcmgNs)
- Towards Structured Multimodal Representations [Workshop Link](https://iclr.cc/virtual/2023/14070)
- Learning Visual Features Enriched by Audio or Language [Workshop Link](https://iclr.cc/virtual/2023/14068)


  ## Multimodal Subtask Graph Generation from Instructional Videos

  ### Problem Definition and Motivation
  - The paper focuses on modeling causal dependencies between subtasks (e.g. wash pan before cooking) from instructional videos depicting real-world procedural tasks.
  - Subtasks often have temporal ordering constraints and preconditions. Modeling these as a graph can help understand the underlying structure of tasks.
  - Challenges arise due to missing subtask annotations and ambiguity in defining dependencies from noisy video data.
  - Prior work has limitations in handling noise and learning expressive graph structures from video.

### Proposed Approach - Multimodal Subtask Graph Generation (MSG2)
MSG2 has two main components:
Multimodal subtask state prediction module: 
1. Uses both video frames and text transcripts to predict if a subtask is not started, in progress, or completed at each time step. Helps compensate for missing subtask annotations.
2. Graph generation module: Employs complexity-regularized inductive logic programming to construct graphs from predicted subtask states. Avoids overly complex graphs.
 - For state prediction, visual features from CLIP and textual features from ASR are fused via multi-head attention. Ordinal regression loss is used to model subtask states.
-  For graph generation, preconditions are learned layer-wise using decision trees, transformed into logic expressions, and consolidated into a final graph. Complexity regularization prevents overly complex preconditions.

  ## Experiments

  - MSG2 evaluated on the ProceL and CrossTask instructional video datasets with human subtask annotations.
  - Produces graphs closer to human annotations than prior inductive logic programming and transformer-based methods.
  - Downstream evaluation on the next subtask prediction shows 30-85% higher accuracy over video transformer baselines like ViViT and STAM.
  - Demonstrates utility of predicted graphs for modeling task structure.

## Limitations and Future Work

  - Performance still relies on the quality of predicted subtask states. Errors propagate to the graph.
  - Significant gaps remain compared to human-annotated graphs.
  - Future work includes enhancing multimodal understanding and incorporating human feedback.

    In summary, the paper presents a novel approach for learning subtask dependencies from noisy instructional videos by robustly combining multimodal signals and graph structure learning. The generated graphs demonstrate usefulness for downstream prediction.




### Group Members
  - Chandramani
  - Sushant Karki
