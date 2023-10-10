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

### Open Challenges 

One open challenge is scaling up the graph learning to much longer, more complex tasks with far more subcomponents. The current approach may face difficulties as the search space grows exponentially. Exploration of more hierarchical or abstract graph representations could help address this.

### Conclusion
Being able to learn graphical representations of tasks and procedures from videos could significantly aid robot learning and planning. Instead of relying solely on hand-engineered task models, robots could automatically construct procedural models from observing humans. These learned models, akin to flowcharts or recipes, could inform planning algorithms. Robots could use them to determine valid step orderings, identify preconditions and dependencies, and decide on the next appropriate action to take. This could greatly expand robots' capacities to perform new, multi-stage tasks by leveraging widely available video data. While the current paper focuses on human activity videos, the methods could eventually be applied to robot-centric instructional videos or human-robot demonstrations.



## Understanding the Modality Gap in CLIP:

### Connection to the Main Theme

This paper investigates the "modality gap" phenomenon observed in CLIP, a popular multimodal contrastive representation learning method. The modality gap refers to the separation between image and text embeddings in the joint latent space. Understanding the causes of this gap relates to the broader challenges of effectively combining representations across modalities in MRL.

### Technical contributions of the paper 

The main technical contributions are:

- Proof-of-concept experiments on a 3D sphere showing local minima in the CLIP loss function that induce distinct disjoint rings, believed to be analogous to the modality gap.
- Analysis showing the CLIP loss has conflicting alignment and uniformity terms that push modalities apart.
- Linear separability experiments indicating complete disjointness of text and image embeddings in CLIP.
- Initialization experiments highlighting sensitivity of gap to initialization criteria.
  
### Our Opinion

The experiments provide compelling evidence that the modality gap arises from properties of the CLIP loss landscape, rather than just initialization. The analysis clearly explains the tension between alignment and uniformity in the loss function. The study gives useful insight into the difficulties of avoiding local minima in high dimensions. However, more investigation is still needed to fully understand the complex minima in real CLIP models.

### Open Challenges 

Key open challenges include scaling up the analysis to higher dimensional spaces, more thoroughly characterizing the loss landscape and minima, and developing techniques to avoid or escape from the local minima leading to the modality gap. On the application side, the impact of the gap on downstream task performance remains unclear.

## Conclusion

Concluding remarks discussing the connections with decision-making for robotics (2 paras)
The modality gap could significantly impact robotics systems that rely on learned multimodal representations from vision, language, and other sensor data. For effective decision-making, robots need to connect perceptions across modalities and understand concepts consistently regardless of the mode of input. However, disjoint representations would limit this cross-modal reasoning, restricting the flexibility of the robot. For instance, a home robot told to "grab the brush" needs to link those words to its visual perception of a brush. The modality divide could break this association between linguistic and visual concepts. Understanding and closing the gap is thus crucial for robotics. This paper provides useful insights into the underlying causes, motivating further research to resolve this issue.


### Group Members
  - Chandramani
  - Sushant Karki
