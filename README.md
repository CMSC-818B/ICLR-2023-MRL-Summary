# ICLR 2023 Multimodal Representation Learning Workshop Summary
Summary of the ICLR 2023 Multimodal Representation Learning Workshop


## Worshops covered

- A Picture is Worth a Thousand Words: Language Models Plan from Pixels [Paper](https://openreview.net/pdf?id=3hTpRkGohE)
- Multimodal Subtask Graph Generation from Instructional Videos [Paper](https://openreview.net/pdf?id=zJhWyDcmgNs)
- Towards Structured Multimodal Representations [Workshop Link](https://iclr.cc/virtual/2023/14070)
- Learning Visual Features Enriched by Audio or Language [Workshop Link](https://iclr.cc/virtual/2023/14068)



## Multimodal Subtask Graph Generation from Instructional Videos

### Connection to the Main Theme

This paper tackles the challenge of learning from multimodal instructional videos containing both visual frames and narrated text. It aims to model the underlying subtask structure and dependencies, which requires effectively combining signals from the different modalities. This relates to the broader theme of multimodal representation learning and how to integrate information across modalities.

### Technical contributions of the paper 

The main technical contributions are:

- A multimodal subtask state prediction module that combines visual and text features to predict missing subtask states and labels in the noisy video data.
- A complexity-regularized inductive logic programming method to generate the subtask graph from the enhanced subtask state labels. It constrains the complexity of the learned graph structure to handle noise.


### Our Opinion
The multimodal state prediction module demonstrates a principled approach to handling missing data by leveraging cross-modal signals. The graph generation method also tackles the challenge of learning interpretable structures from extremely noisy inputs. The complexity regularization helps prevent overfitting to spurious patterns. Overall the techniques seem well-motivated for the problem. Quantitative and qualitative results validate the benefits of the approach.

### Challenges mentioned in the paper

One open challenge is scaling up the graph learning to much longer, more complex tasks with far more subcomponents. The current approach may face difficulties as the search space grows exponentially. Exploration of more hierarchical or abstract graph representations could help address this.

### Conclusion
Being able to learn graphical representations of tasks and procedures from videos could significantly aid robot learning and planning. Instead of relying solely on hand-engineered task models, robots could automatically construct procedural models from observing humans. These learned models, akin to flowcharts or recipes, could inform planning algorithms. Robots could use them to determine valid step orderings, identify preconditions and dependencies, and decide on the next appropriate action to take. This could greatly expand robots' capacities to perform new, multi-stage tasks by leveraging widely available video data. While the current paper focuses on human activity videos, the methods could eventually be applied to robot-centric instructional videos or human-robot demonstrations.


### Group Members
  - Chandramani
  - Sushant Karki
