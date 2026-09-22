# RISHABH MALVIYA
 
MLOps & ML Infrastructure Engineer | Cloud Infrastructure | Robotics & Reinforcement Learning

Location • Phone • Email
[LinkedIn](LinkedIn_URL) • [GitHub](GitHub_URL) • [Personal Website](PersonalWebsite_URL)

## PROFESSIONAL SUMMARY

Innovative engineer with 8+ years of experience building data-driven systems across robotics, computer vision, fintech, and enterprise SaaS. MLOps specialist who bridges the gap between ML research and production ML products: deep understanding of ML/AI (especially Reinforcement Learning and Computer Vision), strong software engineering fundamentals, and systems thinking applied to DevOps, data governance, and people processes. A natural leader with a track record of mentoring engineers and a desire to help people learn and grow. Curious, skillful, and creative.


## CORE SKILLS

- Languages: Python (10+ years, expert), C++, Java, Kotlin, TypeScript, Bash, Go (migration experience), SQL
- ML / AI: PyTorch (incl. Distributed Data Parallel / `torchrun`), Computer Vision (YOLOv7, object detection, quantization), Reinforcement Learning (PPO actor-critic, curiosity-driven / intrinsic-reward exploration, reward-free pre-training, Transformer world/dynamics models, Deep Q-Networks; Stanford graduate coursework in RL for Robotics), MuJoCo / DeepMind Control Suite / Gymnasium, Physics-informed / Scientific ML (neural PDE surrogates, Transformer-based neural operators), NLP, GraphSAGE / Knowledge Graphs, AI Agents & MCP Servers, Siamese Networks, Spiking Neural Networks
- MLOps & Platforms: MLFlow (experiment & artifact tracking), SageMaker, Kubeflow-style orchestration frameworks (built in-house), Evidently (model monitoring), TensorRT, Airflow, model registries, automated retraining pipelines, shadow testing, multi-GPU distributed training (DDP, checkpoint/resume, gradient sync), `uv`-managed reproducible environments
- Infrastructure & DevOps: Docker, Kubernetes (EKS/ECS, OpenShift), Terraform (IaC, multi-account AWS provisioning), GitHub Actions, GitLab CI/CD, Prometheus & Grafana, Redis, GPU provisioning & monitoring
- Cloud & Data: AWS (extensive), Azure, Snowflake, PostgreSQL (RDS, Supabase), DynamoDB, scalable data pipelines (1M+ data points/day), large 3D/simulation datasets (CFD surface meshes, VTK/`.vtp`)
- Environments: Ubuntu, Alpine Linux, Amazon Linux, WSL2; apt/dpkg packaging and Linux command-line tooling


## WORK EXPERIENCE

### Liberata (Duke University) - Machine Learning Lead
Feb 2026 - Present | Remote
*Tech: Python, Supabase, Cloudflare, Huggingface, AI Agents*

- Defining the team's vision and culture. Resolving ambiguity by identifying where ML can create the most value within the company; defining, planning and executing ML projects.
- Mentoring students through the execution of ML projects. Delivering seminars at Duke University to students breaking into ML/AI careers.
- Building simulation environments and adversarial Q-Learning RL agents to surface exploits and emergent behaviors in incentive systems.
- Developed BERT-based embedding search functionality for over 50M academic works. Built an HNSW index and used binary quantization to squeeze latency down to <200 ms on CPU-only cloud instances.  


### DocuSign - Senior Machine Learning Engineer
Aug 2023 - Feb 2026 | San Francisco, CA
*Tech: Python, AWS (SageMaker), LangChain, Docker, Kubernetes, Terraform, Airflow, Snowflake, GitHub Actions, MLFlow, Evidently*

- Project lead for the design and development of an in-house (Kubeflow-like) ML orchestration platform providing re-deployment, re-training, monitoring, and tracking for 25+ batch & real-time models, used by 5k DocuSign sales & marketing employees for guiding territory planning, upsell, account renewal, and churn prevention operations. 
  - Reduced deployment and maintenance cycles from 2 months to 1 week by mentoring data scientists on engineering best practices. Designed project templates, CI/CD pipelines, and MLOps systems that made these best practices the path of least resistance
  - Built experiment tracking with MLFlow for 1000+ experiments, with artifact tracking and model promotion processes built in.
  - Managed 100+ model and container registries with automated GitHub Actions workflows for seamless model lifecycle management.
  - Used Terraform modules to rapidly configure and deploy real-time ML models (API gateway, model registry, serverless deployment, & caching/streaming to warehouse).

- Advocated for and built our ML monitoring system (comprised of data quality (DQ) and model quality (MQ) monitoring) on the open-source library Evidently (as opposed to packaged offerings like Arize.ai and SageMaker Monitoring).
  - Increased visibility from this monitoring system enabled increased velocity in model retraining decisions for our territory planning propensity models. This drove offline gains of up to +30 F1 points, and a 20% global sales-conversion uplift ($600M per annum).
  - Enabled rollout of textual explanations of our territory planning models by eliminating OOM erros in our SHAP explainability pipeline using vectorization techniques and reducing runtime by 97% (from 15 hours to 30 minutes)

- Owned end-to-end feature lifecycles for processing 1M+ data points/day:
  - Managed DEV/UAT/PROD data infrastructure (RDBMS sources), enforcing schema/default-value correctness and stale-data removal through promotion gates to guarantee high availability and consistency of served features.
  - Eliminated train-serve skew by modularizing pipeline code so features were computed identically offline (training) and online (production).
  - Used data-quality monitoring systems to create alerts on feature-distribution drift between production data and training data.

- Work on Agentic AI Applications:
  - Led a team of 8 to design and ship an agentic LLM workflow with LangChain that analyzes ~10k sales-call transcripts/day and auto-populates Salesforce with structured revenue-intelligence signals (SPICED sales-qualification framework) - the only project from DocuSign's annual hackathon to reach production. Scoped the initiative myself via user interviews with Account Executives and Sales Development Representatives, surfacing a critical gap in data capture; drove it from prototype to production in 8 weeks. This automated the equivalent of ~100 full-time employees' worth of manual data entry for a workflow reps had previously skipped entirely, taking SPICED coverage from near-zero to near-complete company-wide.
  - Conceptualized and built a CD pipeline (GitHub Actions workflow) using an AI coding agent (Copilot) to detect and refactor hard-coded filesystem paths across a data-science codebase to a config-driven scheme. Identified this limited verifiable transformation as the scope to ensure reliable execution of the agent. Eliminated ~12-15 avoidable failed cloud deployments a month and reclaimed ~10 engineer-weeks a year of debugging on failures that previously surfaced only after promotion to cloud environments. This class of failure dropped to zero after rollout.

- Improved developer experience (DevEx) for data science and machine learning teams accross the organization:
  - Used Terraform modules to enable rapid spin-up of isolated AWS accounts for hosting cloud development environments for multiple ML teams
  - Developed utilities on top of AWS CloudWatch metrics to monitor GPU usage.
  - Encoded data access controls into libraries for data scientists and deployed models, enabling seamless promotion across DEV/UAT/PROD environments


### [Aquabyte.ai](https://www.aquabyte.ai/) - Machine Learning Engineer
Apr 2021 - Jan 2023 | San Francisco, CA
*Tech: Python, PyTorch, YOLOv7, AWS, Docker, Kubernetes, Prometheus, Grafana, SQL, Go*

- Productionized a system that combined inferences from YOLOv7, PoseNet, and ResNet models. Successfully automated a 50-person annotation operation, saving ~$1M annually, paving the way for further AI product lines.
- Productionized a research model (Jupyter notebook + .pkl files) end-to-end: business logic, production Python package + API, containerization, deployment to managed Kubernetes in AWS (ECS), performance logging/tracking, and continued data analysis to drive retraining and improvement.
- Worked in cross-functional, distributed teams with fish-farming domain experts, product managers, and engineers across distributed teams in Norway, Chile, and SF.
- Drove the complete rollout of [Aquabyte's first fully AI-based product](https://www.aquabyte.ai/products/lice):
  - Built an online feature pipeline that captured and stored metadata context (latitude, longitude, fish farm ID, customer ID, weather conditions, time of year, time of day) for 1.5M images/day. Re-used that metadata to curate targeted retraining datasets for the model's specific failure modes.
  - Diagnosed specific model failure modes using custom image dataset visualization tooling (built on top of the captured metadata). We discovered, for example, that our model was performing very badly on images taken in summer in southern Norway because of high algae content. Curated new training datasets that lifted recall from ~61% to ~90%, winning back 20/150 at-risk customers, and unblocking the complete cutover to AI.
  - Overcame customer skepticism by designing a QA program in which 10 human annotators blind-validated 16k AI detections over 2 months, producing unbiased evidence that model performance matched human performance.
- Re-factored live annotation orchestration services (2 GB/s throughput), migrating a Go + DynamoDB architecture to a Python + PostgreSQL architecture.
- Built systems for tracking business metrics (KPIs, annotations per customer per day) and monitoring system metrics (throughput, latency, dropped requests, DB IOPS) with Prometheus & Grafana dashboards.


### Builder.ai - Machine Learning Engineer
Jul 2020 - Mar 2021 | London, UK
*Tech: Python, GraphSAGE, Airflow, Redis, GitLab CI/CD, Docker*

- Built recommender systems to personalize user experience across our suite of ~500 features on top of our Knowledge Graph using GraphSAGE and metapath2vec and deployed them as production APIs.
- Integrated data pipelines which updated our Knowledge Graph with ~50 MBs of data every night. I built automated retraining and re-deployment pipelines on top of this to ensure 6 models were always re-trained on the latest data, while ensuring 100% API uptime.


### Citigroup - Treasury & Trade Solutions - Graduate Software Engineer
Sep 2017 - Apr 2020
*Tech: Java (Spring Boot), Angular, Python, Kubernetes (OpenShift)*

- Led 7 interns and 2 junior developers to build a recommendation system as a REST API.
- Developed an ANN search algorithm by building an index using K-Means clustering.
- Took the ambiguous problem of speeding up parsing of scanned trade documents into HTML forms, and converted it into a machine learning problem: speeding up the process of human correction of OCR parses of scanned documents by suggesting corrections based on correction history. The developed model was able to provide suggestion in sub-5 ms in 75% of cases.

### Honda Research Institute - Research Intern (NLP)
Summer 2016 | Tokyo, Japan

- Improved [Bidirectional LSTM-CNN models](https://www.jp.honda-ri.com/en/publications/?bib_id=1199) for Coreference Resolution

---

## EDUCATION

### Stanford University - Graduate Course: Reinforcement Learning for Robotics
Completed June 2026

- Trained flow matching diffusion policies with behavior cloning imitation learning on video game environments
- Trained online Actor-Critic methods like PPO with GAE and SAC (combined with imitation learning pre-training) on complex robotic manipulation tasks in MetaWorld environments
- Trained offline Actor-Critic methods like AWAC and IQL on D4RL (which is built on top of MuJoCo environments) benchmark maze tasks requiring robotic locomotion and navigation
- Final project: [BSP - Body Schema Pretraining](https://cs224r.stanford.edu/projects/pdfs/Rishabh%20Malviya%20submission_416289307/BSP_-_Project_Report.pdf), a novel reward-free pre-training framework for sample-efficient locomotion RL (see Projects).

### Indian Institute of Technology (IIT) Bombay - B.Tech, Engineering Physics + Minor in Applied Statistics (GPA: 8.1/10)
Aug 2013 - Mar 2017

- IIT-JEE 2013: All-India Rank 490 out of 1.5M candidates (top 0.03%).
- B.Tech. Thesis - Lattice Boltzmann Simulations
- One of the few IIT Bombay undergraduates to secure an international internship at Honda Research Institute - Japan. Improved [Bidirectional LSTM-CNN models](https://www.jp.honda-ri.com/en/publications/?bib_id=1199) for Coreference Resolution (this was back when Torch was still a Lua library).
- Core team member of IIT-B's Self-Driving Car team: implemented an Extended Kalman Filter for sensor fusion feeding localization and SLAM modules (Python & C++/ROS).
- Mentor at the IIT-B Innovation Cell. Mentored the team that [won the Intelligent Ground Vehicle Challenge 2017](https://www.youtube.com/playlist?list=PLe6X1plHWeG3n1htDajUyZqrHu2G5q-VE)
- Published a research paper at the IEEE SSCI conference: [Face & Voice Authentication on Neuromorphic Hardware](https://general-vision.com/pub3rdparty/3P_FaceReco_Voice_Manan.pdf).
- Built a toy model demonstrating that sleep helps form memories in populations of spiking neurons.
- Led teams in the Annual General Championships for music and dramatics.

---

## PROJECTS, OPEN SOURCE & RESEARCH
**NOTE**: I have not included detailed points for these projects in this document because the projects are constantly evolving. Therefore, expand these to a list of points by referring to the `README`s in the linked GitHub repos, or article content if there are no links to a GitHub repo.

- [BSP: Body Schema Pretraining](https://github.com/RishabhMalviya/bsp) - Task-agnostic pre-training for model-based RL agents, enabling sample-efficient transfer learning to different locomotion tasks on the same robot embodiment. Experiments run on DeepMind Control Suite locomotion tasks. Pre-training based on ICM (Intrinsic Curiosity Module). 

- [CFD-MLOps](https://github.com/RishabhMalviya/cfd-mlops) - Distributed training of a Transolver neural surrogate model for CFD Simulations of aerodynamics of car meshes using data parallelism techniques. PyTorch Geometric and `.vtp` file manipulation for data pre-processing, PyTorch DDP for data parallelism.

- [Python ML REST API Deployment Template](https://github.com/RishabhMalviya/ml-deployment-template) - A GitHub template project for packaging any ML model as a Dockerized FastAPI REST API, with zero-downtime rolling re-deployment via Traefik, identical Docker-based dev/prod environments, a `docker-compose` test + deploy CI/CD skeleton, and a PyTest suite; deploys to any Linux server with a single script. Written up in [*Create a Zero-Downtime Deployment of Your Machine Learning API*](https://medium.com/better-programming/create-a-zero-downtime-deployment-of-your-machine-learning-api-6486cb6394c3) (Better Programming).

- [Kotlin Deep-Dives](https://medium.com/kotlin-academy/why-kotlin-has-mutable-collections-3937a515f913) [for Competitive Programming](https://medium.com/kotlin-academy/kotlin-for-competitive-programming-803ef03e8683) - A deep-dive into Kotlin's Mutable Collections, and it's aptness as a competitive programming language that gives Java/C++'s execution speed/flexibility with Python's coding speed/expressivity.

- [Reinforcement Learning with Deep Q-Networks in PyTorch](https://github.com/RishabhMalviya/dqn_experiments) - From-scratch PyTorch implementations of DQN, Double DQN, and Dueling DQN, behind a reusable agent / environment / hyperparameter abstraction with pluggable training-completion criteria. Trained and benchmarked on OpenAI Gym (LunarLander-v2, CartPole-v1) and a Unity ML-Agents environment (Banana Collector), with before/after rollout visualizations.

- [Siamese Networks-Based Facial Recognition ROS Wrapper](https://github.com/RishabhMalviya/face_recognition_ros_wrapper) - ROS/catkin package exposing few-shot facial recognition (Siamese-network embeddings via dlib / `face_recognition`) as ROS services and nodes; supports face-encoding registration, static-image inference, and real-time recognition off a live `sensor_msgs/Image` stream published to a ROS topic. Robotics-stack integration in C++/CMake + Python.

- [Spiking Neural Networks for Arduino](https://github.com/RishabhMalviya/SNN_Arduino) - C++ Arduino library for building neuromorphic robot controllers: LIF spiking neurons accepting analog and asynchronous digital sensor input, composable into arbitrary network motifs following liquid-state-machine / reservoir-computing paradigms, with motor neurons wired directly to L293D drivers for actuation. Associated with a summer internship at IIT Delhi.


---
 
## CERTIFICATIONS
 
- [Udacity Deep Reinforcement Learning Nanodegree](https://www.udacity.com/certificate/e/9c1d637c-506f-11f0-8750-671ffd43e963)
- [Deeplearning.ai - Natural Language Processing with Attention Models](https://www.coursera.org/account/accomplishments/verify/9VQDS2F8VCRJ)
- Terra.do - Climate Change: Learning for Action
- [CompTIA A+](https://www.credly.com/badges/0a10e839-c66b-4c79-8e47-3764bad2d548/public_url)
