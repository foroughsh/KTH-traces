# Traces and datasets overview
This repository includes data sets used to develop and evaluate data-driven methods for network analysis. The results of these analyses are published in several research papers and theses. We collect all traces from real testbeds (described in the presented papers) by running applications under different load patterns. 

Data traces **"VoD periodic - CNSM 2015.zip"** and **"VoD flashcrowd - CNSM 2015.zip"** are first collected and used for the research published in:
1) R. Yanggratoke, J. Ahmed, J. Ardelius, C. Flinta, A. Johnsson, D. Gillblad, and R. Stadler, “Predicting Service Metrics for Cluster-based Services using Real-time Analytics,” in Network and Service Management (CNSM), 2015 11th International Conference on. IEEE, 2015, pp. 135–143.

Date traces **"KV flashcrowd - JNSM 2017.zip"** and **"KV periodic - JNSM 2017.zip"** are first collected and used for the research published in:
2) R.  Stadler,  R.  Pasquini,  and  V.  Fodor,  “Learning  from  network  device statistics,” Journal of Network and Systems Management, vol. 25, no. 4, pp. 672–698, 2017.

These research papers describe the testbed and the KV and VoD services. Later we use these data sets for the following research papers:

2) Forough Shahab Samani, Rolf Stadler. "Predicting Distributions of Service Metrics using Neural Networks," 14th International Conference on Network and Service Management (CNSM), 2018.
3) Forough Shahab Samani, Rolf Stadler, Andreas Johansson, Christofer Flinta, "Demonstration: Predicting Distributions of Service Metrics," IFIP/IEEE Symposium on Integrated Network and Service Management (IM), 2019.
4) Forough Shahab Samani, Hongyi Zhang, Rolf Stadler, "Efficient Learning on High-dimensional Operational Data," 15th International Conference on Network and Service Management (CNSM), 2019.
5) Forough Shahab Samani, Rolf Stadler, Christofer Flinta, Andreas Johansson, "Conditional Density Estimation of Service Metrics for Networked Services," IEEE Transactions on Network and Service Management, 2021.
6) Xiaoxuan Wang, Forough Shahab Samani, Rolf Stadler, "Online feature selection for rapid, low-overhead learning in networked systems," 16th International Conference on Network and Service Management (CNSM), 2020.
7) Xiaoxuan Wang, Forough Shahab Samani, Andreas Johnsson, Rolf Stadler, "Online feature selection for low-overhead learning in networked systems," 17th International Conference on Network and Service Management (CNSM), 2021.
8) Zhang, Hongyi. "Efficient learning on high-dimensional operational data." (2019).
9) Xiaoxuan Wang, “Dimensionality reduction for performance prediction in networked systems,” master thesis, KTH Royal Institute of Technology, 2020.
10) Tang Chen, "Forecasting Service Metrics for Network Services," master thesis, KTH Royal Institute of Technology, (2020).

Another set of data traces (**"data - CNSM 2022 - TNSM 2024.zip"**) is related to a microservice-based application developed by Forough Shahabsamani presented in [our framework and application](https://github.com/foroughsh/A_framework_for_meeting_MO_TNSM2023) and [application use case of the framework](https://github.com/foroughsh/online_policy_adaptation_using_rollout). We deploy this application as our testbed which is explained mainly in the following publications:

11) Forough Shahab Samani, Rolf Stadler, "Dynamically meeting performance objectives for multiple services on a service mesh," 18th International Conference on Network and Service Management (CNSM), 2022.
12) Forough Shahab Samani, Rolf Stadler, "A Framework for dynamically meeting performance objectives on a service mesh". IEEE Transactions on Network and Service Management, 2024.
13) Forough Shahab Samani, Kim Hammar, Rolf Stadler, "Online Policy Adaptation for Networked Systems using Rollout," NOMS 2024-2024 IEEE/IFIP Network Operations and Management Symposium, 2024.
14) Forough Shahab Samani, Hannes Larsson, Simon Damberg, Andreas Johnsson, Rolf Stadler, "Comparing Transfer Learning and Rollout for Policy Adaptation in a Changing Network Environment," NOMS 2024-2024 IEEE/IFIP Network Operations and Management Symposium, 2024.
15) Laura Macià Coll, "Efficiently Learning the System Model for Microservice-based Applications," master thesis, KTH Royal Institute of Technology, (2024).

The last set of traces is related to an open-source application called "online boutique" (https://github.com/GoogleCloudPlatform/microservices-demo). This data set is collected by Maria Halvarsson. The data set is **"Online_boutique_application.zip"**. These datasets are explained and used in Maria's thesis.

16) Maria Halvarsson, "Learning End-to-End QoS Metrics for a Microservice Application," master thesis, KTH Royal Institute of Technology, (2024).

# Example: Traces used in TNSM2024 paper "A Framework for dynamically meeting performance objectives on a service mesh"
As we describe in more detail on these two pages [our framework and application](https://github.com/foroughsh/A_framework_for_meeting_MO_TNSM2023) and [application use case of the framework](https://github.com/foroughsh/online_policy_adaptation_using_rollout), in this paper, we describe a framework designed to control networked systems automatically. In this framework, we follow 6 steps:
1) Select a scenario and formulate the RL model
2) Run the scenario on the testbed and collect monitoring data
3) Use monitoring data and learn the system model
4) Simulate the scenario and learn the control policy
5) Evaluate learned policy on the simulator
6) Evaluate learned policy on the testbed

In this paper, an extension of the CNSM 2022 paper, "Dynamically Meeting Performance Objectives for Multiple Services on a Service Mesh", we define four scenarios to evaluate the developed framework, along with an additional scenario to assess the baseline approach using Kubernetes HPA (Horizontal Pod Autoscaling). The trace data for the first three scenarios is stored in the file **data_CNSM_2024.csv**, while for the fourth scenario, we use the trace data from **data_TNSM_2024.csv**. The evaluation for the baseline is presented in **TNSM_2024_evaluations.zip**, folder sc5.

To gather these traces from the testbed, we conducted experiments, monitoring the system for a specific duration (refer to [data collection](https://github.com/foroughsh/A_framework_for_meeting_MO_TNSM2023/tree/master/src/A_framework_for_meeting_MO_TNSM2023/data_collection)). The collected trace is then used to learn the system model (see [training the system model](https://github.com/foroughsh/A_framework_for_meeting_MO_TNSM2023/tree/master/src/A_framework_for_meeting_MO_TNSM2023/system_model)). Using this system model, we set up a simulator to train a reinforcement learning (RL) agent (see [train RL agent](https://github.com/foroughsh/A_framework_for_meeting_MO_TNSM2023/tree/master/src/A_framework_for_meeting_MO_TNSM2023/learn_ppo_policy)). Once the control policy is learned, we evaluate it on the simulator using the traces employed for generating the paper's figures. Finally, the learned policy is copied to the testbed for evaluation of the policy on the real system. Traces for evaluation of the learned policies presented in the paper are added with the name **TNSM_2024_evaluations.zip**.
