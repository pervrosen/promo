---
title: "Data poisoning"
date: 2023-03-14T12:37:53+01:00
image: pic16.jpeg
draft: false
publishDate: 2023-03-15
---

## Data poisoning

**Detta är ett mycket specifikt område inom MLOps och pga ett sk. Domain Specific Language (DSL) håller jag denna genomgång på engelska**

Data poisoning is a technique used by attackers to manipulate a machine learning model by intentionally injecting malicious or incorrect data into the training process or as feedback data. The goal of data poisoning is to cause the model to make incorrect predictions or classifications, leading to undesirable outcomes.

In the context outlined above, the risk of data poisoning can occur if attackers intentionally feed incorrect or malicious data to the model during the training process or during its production, and must be taken seriously. If the model is trained on unverified data or if feedback data from users is not properly monitored, this could lead to the model learning from incorrect or biased data, resulting in poor performance or incorrect predictions.

To prevent data poisoning, it is essential to ensure that the training dataset is clean and free of malicious or incorrect data. This can be done by verifying the data before it is used to train the model. Additionally, it is important to monitor feedback data from users and ensure that it is properly labeled and validated before it is used to retrain the model. An idea can be to give a percentage weight to its validity as a feature to the model if we cannot select binary.

Another method to prevent data poisoning is by implementing robust machine learning algorithms that can detect and filter out malicious data. This can include methods such as outlier detection and anomaly detection, which can identify unusual patterns in the data and remove them from the training dataset.

Overall, preventing data poisoning requires a combination of careful data selection, robust machine learning algorithms, and ongoing monitoring of feedback data from users. By taking these steps, organizations can ensure that their AI models are trained on reliable data and are less vulnerable to attacks.

### We elaborate on some of the algorithms

Here, I present some examples of robust machine learning algorithms that can help detect and filter out malicious data:

* Robust Principal Component Analysis (RPCA): RPCA is a technique used to decompose a dataset into low-rank and sparse components. The low-rank component represents the underlying structure of the data, while the sparse component represents the noise or outliers in the data. By applying RPCA, it is possible to identify and filter out the malicious data points that do not conform to the underlying structure of the data.

* Isolation Forest: Isolation Forest is an algorithm that uses decision trees to isolate and remove outliers from a dataset. The algorithm works by recursively partitioning the dataset into subsets and isolating the outliers in the smallest partitions. This method is particularly effective at identifying and removing data points that are far from the majority of the data.

* One-Class SVM: One-Class SVM is a type of support vector machine that is used for outlier detection. The algorithm works by defining a boundary around the majority of the data points and identifying any data points that fall outside of this boundary as outliers. This method is particularly useful for detecting and removing data points that are significantly different from the majority of the data.

* Deep Autoencoder: Deep Autoencoder is a type of neural network that is used for unsupervised feature learning. The algorithm works by learning to reconstruct the input data using a compressed representation of the data. By training the autoencoder on a clean dataset, it is possible to use it to detect and filter out malicious data points that do not fit the learned representation of the data.

There are many other robust machine learning algorithms that can be used to detect and filter out malicious data, and the best approach will depend on the specific application and dataset.

### Data poisoning in chat bots

The techniques I mentioned earlier are more commonly used for detecting and filtering out malicious data in general, including fraudulent activities such as money laundering. However, there are several techniques that can be specifically applied to chatbots to prevent wrong answers from being fed back into the system. Here are a few examples:

* Confidence Thresholds: Chatbots can be designed to only provide responses that are above a certain confidence threshold. For example, if the chatbot is only 80% confident in its response, it may ask the user to clarify their question or provide additional information before giving a response. This can help prevent incorrect responses from being fed back into the system.

* Error Analysis: Chatbots can be designed to analyze the types of errors that are commonly made and use this information to improve the system. For example, if the chatbot frequently provides incorrect answers to questions about a specific topic, it may indicate that the chatbot needs more training data or that the data it has been trained on is biased. By identifying and addressing these errors, the chatbot can improve its accuracy over time.

* Human-in-the-Loop: Chatbots can be designed to have a human-in-the-loop to review and validate responses. For example, if the chatbot is unsure about a response or if the response is particularly important, it may ask a human to review the response and confirm its accuracy. This can help ensure that incorrect responses are not fed back into the system.

* Regular Retraining: Chatbots can be regularly retrained on new data to improve their accuracy and prevent incorrect responses from being fed back into the system. This can involve collecting feedback from users and using this feedback to improve the training data or the chatbot's algorithms.

Overall, preventing wrong answers from being fed back into chatbots involves a combination of designing the chatbot to have appropriate confidence thresholds, conducting error analysis, incorporating a human-in-the-loop, and regularly retraining the system. By taking these steps in a formalized process, chatbots can improve their accuracy and provide more reliable responses to users.

### A small list of use cases and the current popular AI toolset used

* Fraud Detection - 
Approach: Isolation Forest, One-Class SVM, or Deep Autoencoder can be effective at identifying fraudulent transactions or activities that deviate from normal behavior.

* Spam Detection - 
Approach: Naive Bayes or Logistic Regression can be used to classify emails or messages as spam or not spam, based on their content and metadata.

* Outlier Detection - 
Approach: Robust Principal Component Analysis (RPCA), Isolation Forest, or One-Class SVM can be used to identify and filter out data points that do not conform to the underlying structure of the data.

* Adversarial Examples Detection - 
Approach: Robust Principal Component Analysis (RPCA) or other techniques can be used to detect and filter out adversarial examples in image recognition tasks.

* Malware Detection - 
Approach: Supervised learning techniques such as Random Forests, Support Vector Machines (SVMs), or Deep Learning techniques can be used to detect and classify malware based on its behavior or code.

* Social Media Content Moderation - 
Approach: Machine learning techniques such as Text Classification, Named Entity Recognition (NER), or Sequence Labeling can be used to identify and filter out offensive or inappropriate content.

* Chatbot Quality Control - 
Approach: Confidence thresholds, error analysis, human-in-the-loop, and regular retraining can be used to improve the accuracy of chatbots and prevent incorrect responses from being fed back into the system.

It's important to note that the best approach will depend on the specific application and dataset, and it's always a good idea to experiment with multiple techniques and compare their performance to determine the best approach for your specific use case on a regular basis.

The process including the activity of cleaning feedback data is important due to the above reasons. You can read more about how to fit this activity in a development process in the link attached below.

För vidare information: [MLOps och AIOps förklarad och dess processkomponenter](https://ai-tankesmedjan.onrender.com/aiops)
