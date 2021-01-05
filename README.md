# MAADS-VIPERviz

Visualize streaming insights over conventional web browers using HTTPS with websockets.

MAADS-VIPERviz is visualization technology to visualize results from HPDE.  Specifically, HPDE will apply machine learning to streaming data for:
1)	Predictive Analytics
a.	Users can visualize these results by calling the file: Prediction.HTML
2)	Prescriptive Analytics or Optimization
a.	Users can visualize these results by calling the file: Optimization.HTML
3)	Anomaly Detection using unsupervised learning
a.	Users can visualize these results by calling the file: Anomaly.HTML

VIPERviz uses websockets to connect to Web browsers over secure HTTPS connections.   Users access the visualization using standard browsers to connect to VIPERviz.  The format of the URL must be the following:

https://[host]:[port]/[HTML file]?topic=[Topic Name] &offset=[Offset, set to 0]&topictype=[anomaly, prediction,optimization,or AIMS]&secure=[1 or 0]&consumerid=[Consumer ID for the topic] &vipertoken=[Viper token]
