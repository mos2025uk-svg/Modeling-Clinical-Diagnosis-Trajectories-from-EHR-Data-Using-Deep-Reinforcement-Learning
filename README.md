# Modeling-Clinical-Diagnosis-Trajectories-from-EHR-Data-Using-Deep-Reinforcement-Learning
Learning diagnostic pathways from electronic health records using deep reinforcement learning. The approach models patient journeys as sequential decision processes, capturing temporal relationships between symptoms, tests, and diagnoses to reveal clinically meaningful diagnostic trajectories and support data-driven decision analysis.
This project explores the use of Deep Reinforcement Learning (DRL) to automatically extract and model diagnosis pathways from Electronic Health Records (EHRs). The system learns sequential clinical decision patterns—such as symptom presentation, diagnostic tests, intermediate diagnoses, and final outcomes—by framing clinical progression as a Markov Decision Process.

Using longitudinal EHR data, the DRL agent is trained to identify optimal diagnostic trajectories that reflect real-world clinical practice. The learned pathways provide insights into common and atypical diagnostic flows, support clinical decision analysis, and enable downstream applications such as outcome prediction, care optimization, and guideline discovery.

Key Objectives

Model patient diagnostic journeys as sequential decision processes

Learn latent diagnostic pathways from high-dimensional EHR data

Capture temporal dependencies between symptoms, tests, and diagnoses

Enable interpretable pathway extraction for clinical and research use

Potential Applications

Clinical decision support

Care pathway optimization

Medical process mining

Healthcare quality and outcome analysis
Motivation and Problem Statement

Modern machine learning classifiers are highly effective at predicting diagnostic endpoints. However, in healthcare, the diagnostic pathway—the sequence of observations, tests, and decisions leading to a diagnosis—is often as important as the final outcome itself. Clinicians rely on these pathways for interpretability, safety, and trust.

This project addresses that gap by developing a Deep Reinforcement Learning model based on Deep Q-Learning (DQN) that not only predicts the final diagnostic outcome but also explicitly learns and outputs the diagnostic pathway followed to reach that endpoint.

Dataset

The dataset used in this project is derived from the research paper “Extracting Diagnosis Pathways from Electronic Health Records Using Deep Reinforcement Learning” by Lillian Muyama, Antoine Neuraz, and Adrien Coulet (submitted May 10, 2023).

The authors synthesized the dataset for the disease anemia by consulting domain experts to identify clinically relevant factors contributing to the condition. A decision tree model was then used to generate realistic diagnostic trajectories. The resulting dataset was split into training and testing sets using an 80/20 split.

Decision Problem Formulation
State Space

The environment state is represented as an observation vector composed of multiple clinical features.

A feature value different from -1 indicates that the feature has been observed.

A value of -1 indicates that the feature is currently unobserved.

This formulation models partial observability commonly encountered in real-world clinical decision-making.

Action Space

The action space consists of two categories:

Diagnosis Actions

Produce a final diagnosis based on the current trajectory.

These actions are terminal and end the episode.

Feature Query Actions

Query the environment to reveal the value of an unobserved feature.

These actions are non-terminal and update the next state with newly observed information.

Reward Structure

Diagnosis Actions

+5 for a correct diagnosis

−100 for an incorrect diagnosis, reflecting the high risk associated with diagnostic errors in healthcare

Feature Query Actions

+1 for querying a new feature, encouraging exploration and information gathering

−1000 for repeating a previously queried feature, strongly discouraging redundant or inefficient behavior
