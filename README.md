# ICLR 2023 Multimodal Representation Learning Workshop Summary
Summary of the ICLR 2023 Multimodal Representation Learning Workshop


## Worshops covered

- Multimodal Subtask Graph Generation from Instructional Videos [Paper](https://openreview.net/pdf?id=zJhWyDcmgNs)
- Understanding the Modality Gap in CLIP [Paper](https://openreview.net/pdf?id=8W3KGzw7fNI)
- A Picture is Worth a Thousand Words: Language Models Plan from Pixels [Paper](https://openreview.net/pdf?id=3hTpRkGohE)
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

### Conclusion

The modality gap could significantly impact robotics systems that rely on learned multimodal representations from vision, language, and other sensor data. For effective decision-making, robots need to connect perceptions across modalities and understand concepts consistently regardless of the mode of input. However, disjoint representations would limit this cross-modal reasoning, restricting the flexibility of the robot. For instance, a home robot told to "grab the brush" needs to link those words to its visual perception of a brush. The modality divide could break this association between linguistic and visual concepts. Understanding and closing the gap is thus crucial for robotics. This paper provides useful insights into the underlying causes, motivating further research to resolve this issue.

## A Picture is Worth a Thousand Words: Language Models Plan from Pixels 


### Summary
This study explores a fascinating intersection of artificial intelligence, language models, and robotics by harnessing the capabilities of Pre-trained Language Models (PLMs) for planning long-horizon tasks. Unlike previous attempts that have utilized PLMs for such purposes, this research takes a unique approach by directly incorporating visual observations into the decision-making process. Through a series of experiments conducted on two embodied agent benchmarks, the authors demonstrate that this novel approach outperforms alternative methods, such as encoding visual observations as text (image captioning), utilizing visual pre-trained affordance functions, or disregarding visual information altogether.

### Connection to the Common Theme
This work aligns seamlessly with the theme of Multimodal Representation Learning. In essence, the authors aim to bridge the gap between visual observations and language-based instruction by learning a unified representation in the same embedding space as the base language model. To achieve this, they employ an observation encoder that transforms raw pixel data from visual observations into embeddings of the same dimensionality as the language model's embeddings. These visual embeddings are then seamlessly integrated with the embeddings of the instructional text. This innovative approach enables the language model to generate actions based on a holistic understanding of both the textual instructions and the visual context derived from the observations.

### Technical Contributions of the Paper
The primary technical contribution of this paper lies in its novel approach to incorporating visual data into the decision-making process of a language model. Instead of relying on conventional methods that either convert visual information into text or use pre-trained affordance functions, the authors opt for a more direct and integrated approach. By learning representations that can be readily understood by the language model itself, this approach streamlines the planning process and eliminates unnecessary conversions or intermediaries.

Furthermore, the research notably refrains from assuming prior knowledge of the possible actions available to the agent, which is a particularly challenging assumption in planning tasks, as it necessitates a mechanism for mapping the actions generated by the language model (in textual form) into concrete signals that can drive the agent's actuators. 

### Opinion on Technical Contributions
This paper's approach, while promising, bears resemblance to the approach used in the PaLM-E paper, which has garnered significant attention in the research community. The popularity of the PaLM-E paper suggests that this approach of representing visual observations in the same latent space as textual embeddings is a positive step in the right direction for advancing the capabilities of language models in multimodal decision-making.

However, a notable point of ambiguity arises from the lack of a clear explanation regarding how the paper maps textual actions generated by the language model to actual signals for the agent's actuators. This aspect remains a crucial piece of the puzzle in the context of embodied agents and warrants further clarification and exploration.


### Open Challenges in Grounding and Multimodal Learning
As the field of using Pre-trained Language Models (PLMs) for planning long-horizon tasks with visual input and robotics continues to evolve, several open challenges remain. These challenges are central to ensuring that AI agents can effectively bridge the gap between language-based instructions and the physical world while optimizing the integration of visual and textual representations.

**1. Grounding Language in the Physical World**

In terms of grounding, there are two key challenges: 

- **Accurate Action Mapping and Actuation:**
Grounding language in the physical world remains a fundamental challenge. Effectively mapping textual actions generated by language models to concrete signals for actuators in the agent's environment is essential. Developing robust mechanisms that ensure that language-based instructions lead to precise and reliable real-world actions is a central challenge in achieving seamless human-AI collaboration and the deployment of AI in real-world scenarios.

- **Safety and Ethical Grounding:**
Ensuring that AI agents make safe and ethical decisions in the physical world requires robust grounding in safety rules and ethical guidelines. Developing mechanisms that ground AI agents' understanding of safety and ethics is critical for preventing harmful actions and ethical violations.

**2. Multimodal Learning approaches of Visual and Textual Representations: Combining vs. Joint Learning**

The integration of visual and textual information is a key enabler for AI agents to understand and act in the real world. Two main options of learning multimodal representations are:

- **Combining Representations:** One approach involves combining separately learned visual and textual representations. This approach relies on pre-trained models for each modality and then fusing the representations. The challenge here is to ensure that the fused representations capture the semantics and relationships between visual and textual elements accurately.

- **Joint Learning:** Another approach is to train models that learn visual and textual representations together in a unified framework. This approach has the advantage of potentially capturing richer cross-modal relationships but requires overcoming challenges related to model architecture, training data, and optimization.

Which approach is the most optimal is still an area of active research and further advancement in this area will directly improve the capabilities of our future agents.

### Conclusion
The emerging consensus in the field suggests that Language Model Models (LLMs) exhibit remarkable capabilities as general-purpose zero-shot planners when provided with appropriate instructions. This development has given rise to an intriguing fusion of language models and robotics, wherein LLMs effectively serve as the "brains" of agents, orchestrating and planning actions for robotic platforms.

Research like the one presented in this paper, with a strong focus on Multimodal Representation Learning, are instrumental in opening new avenues for the synergistic integration of LLMs with robotics. The ability to seamlessly combine textual instructions with visual context not only enhances the autonomy and decision-making capacity of robotic agents but also brings us closer to achieving the vision of intelligent, adaptable robots that can operate effectively in diverse real-world environments.

The intersection of Language Model Models and robotics is an area of ongoing exploration and innovation, with the potential to revolutionize various industries, from healthcare and manufacturing to space exploration and autonomous vehicles. As we continue to delve into these possibilities, the fusion of LLMs and robotics remains an exciting and evolving field that promises to shape the future of automation and intelligent decision-making.



## Learning Visual Features Enriched by Audio or Language

The presentation delves into the realm of Multimodal Representation Learning (MRL), a burgeoning field in AI and machine learning.s. In this presentation, the primary focus is on the intricate fusion of audio-visual and visual-language modalities to address complex tasks, particularly in the domain of video understanding. This theme is emblematic of the broader landscape of MRL, where the advantages and intricacies of harmoniously integrating diverse modalities, such as vision, audio, and language, are thoroughly explored.

### Technical Contributions Unveiled

The core of the talk revolves around an array of ingenious technical contributions that illuminate the path to advanced MRL. Three pivotal ideas take the stage:

- **Harnessing Audio Cues for Visual Scene Augmentation**: The presentation highlights a pioneering approach that leverages audio echoes and spatial signals to enrich the understanding of visual scenes. This self-supervised methodology opens doors to enhanced scene perception, offering unique solutions to the complexities inherent in three-dimensional environment comprehension.

- **Audio Adaptation for Varying Environments**: An innovative technique is introduced, wherein audio data is adeptly transformed to align with distinct visual environments. This adaptation mechanism is a novel solution to the challenge of establishing coherent audio-visual associations, a critical aspect of MRL.

- **Video-Language Embedding Model**: A sophisticated video-language embedding model takes center stage, enabling the encapsulation of both activities and intentions within egocentric video. This ambitious undertaking seeks to bridge the gap between language descriptions and immersive visual experiences, facilitating more comprehensive and contextually aware understanding.

## Technical Contributions

The techniques presented in this talk embody a creative fusion of audio, visual, and language modalities. Notably, the utilization of spatial audio cues for enhancing visual scene understanding represents a groundbreaking approach with immense potential. This approach addresses a critical challenge in the realm of 3D environment perception and promises to enrich the spatial awareness of AI systems.

The concept of adapting audio data to align with specific visual contexts is equally compelling. It has the potential to establish consistent and meaningful audio-visual associations, significantly advancing MRL in scenarios where varying environments are encountered.

The video-language embedding model is another remarkable endeavor, striving to bridge language descriptions with immersive visual inputs. This innovation promises a deeper understanding of actions and intentions within the visual field. However, a more detailed technical exposition is required to comprehensively evaluate the methods and their outcomes.

## Open Challenges and Future Prospects

The talk implicitly acknowledges a set of open challenges that merit attention. Scaling these techniques to the complexity of real-world environments is a formidable task. Ensuring that the learned representations generalize effectively across diverse scenarios and modalities is essential. Moreover, the true test lies in validating whether these multimodal representations indeed lead to performance improvements in practical downstream tasks.

## Implications for Decision-Making in Robotics

The final segment of the presentation extrapolates the significance of these multimodal representation learning techniques to the domain of robotics and embodied AI systems. Robots, tasked with making sense of the world, are reliant on multiple modalities, including vision, audio, and natural language interactions. The coalescence of these modalities into joint representations has the potential to revolutionize how robots perceive and interpret their surroundings, paving the way for more sophisticated decision-making processes.

By learning to associate language instructions with visual and audio inputs, robots can demonstrate heightened flexibility in comprehending verbal commands and executing tasks in intricate real-world environments. While the abstract offers only a glimpse into these promising directions, the emphasis on spatial audio, audio-visual learning, and video-language embedding signifies an encouraging trajectory towards robustly linking modalities to support dynamic decision-making in the realm of robotics.

Continued research and development in this domain hold the promise of ushering in a new era of highly capable and adaptive robotic assistants.


### Group Members
  - Chandramani
  - Sushant Karki
