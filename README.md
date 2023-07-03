# Sequence Anomaly BERT

With the ever-increasing digitalisation of society and the explosion of internet-enabled devices with the Internet of Things (IoT), keeping services and devices secure is becoming more important. Logs play a critical role in sustaining system reliability. Manual analysis of logs has become increasingly difficult, accelerating the development of automated methods for log-anomaly detection. Despite significant progress in automating log analysis, current state-of-the-art methods face challenges dealing with unstable log data, which means that the content of log messages evolves over time.

We show that LogBERT, a state-of-the-art technique based on Bidirectional Encoder Representations from Transformers (BERT), cannot deal with unstable log data. On the three most prevalent publicly available log datasets, Mathew's Correlation Coefficient (MCC) score (which measures the correlation between a model's output and the correct labels) of LogBERT dropped by 90\% after increasing log data instability from 1\% to over 80\% normal sequences containing logkeys in the test set. Log data instability was increased by only reassigning samples between the train and test set. Furthermore, we show that the high performance of LogBERT reported in the original paper was achieved because the model relied on a simple heuristic that only worked under specific conditions.

To address this issue, we propose a novel sequence anomaly detection technique based on BERT: Vocabulary-Free BERT (VoBERT). VoBERT uses a novel pre-training task we designed specifically for anomaly detection: Vocabulary-Free Masked Language Modeling (VF-MLM). We adapted traditional MLM and removed the fixed vocabulary constraint, which allows VF-MLM to classify out-of-vocabulary logkeys correctly.

We highlight that VoBERT is more stable than LogBERT and outperforms the latter in certain situations where log data is very unstable. For the public datasets, the MCC score of the specific train-test split used in the LogBERT paper dropped by 90\% after reassigning the train-test split, increasing log data instability. In addition to sequence-level anomaly predictions, we evaluated all approaches on element level, providing a more granular performance assessment.

To assess the generalisation of the experimental results to real-world scenarios, we conducted a case study evaluating the anomaly detection models on real-world security event data collected at a large bank (50,000+ employees). We found that the simple heuristic did not work for this real-world data, having a negative correlation with the correct results. VoBERT showed performance on par with LogBERT on this real-world security event dataset.

We urge future researchers to evaluate their methods on real-world data, as we showed that the commonly used public datasets do not represent real-world scenarios. Furthermore, it is important to assess how difficult it is to detect anomalies in datasets used for evaluation. When a simple heuristic can perform well, such datasets might not be well suited to evaluate a complex anomaly detection model.

This thesis is a proof of concept for the novel pre-training task VF-MLM and paves the way for future work to refine this technique further, as well as to develop additional robust and adaptable solutions for log and security event anomaly detection.

The implementation is based on LogBERT (https://github.com/HelenGuohx/logbert).
