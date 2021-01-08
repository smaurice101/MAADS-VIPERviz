# MAADS-VIPERviz

Visualize streaming insights over conventional web browers using HTTPS with websockets.

MAADS-VIPERviz is visualization technology to visualize streaming results from Kafka.  Specifically, HPDE will apply machine learning to streaming data and store results in Kafka for:
1)	Predictive Analytics
a.	Users can visualize these results by calling the file: Prediction.HTML
2)	Prescriptive Analytics or Optimization
a.	Users can visualize these results by calling the file: Optimization.HTML
3)	Anomaly Detection using unsupervised learning
a.	Users can visualize these results by calling the file: Anomaly.HTML
4) Algorithms and Insights Management (AiMS): Aims.html

**INSTRUCTIONS:**
1) START: [viperviz binary] [host] [port]
2) Copy the contents of VIEWS.ZIP to the folder **_viperviz/vews_**
3) You must have server and client certificates in the same folder as Viperviz named: client.cer.pem and client.key.pem.  Examples are provided in the ZIP files to get you started but you should have official certificates for HTTPS connections.

Viperviz will listen on [port] for HTTP and [port]+1 on HTTPS connection.  For example, if you run viperviz on port 8000, it will accept HTTP connections on port 8000, and HTTPS connections on port 8001.

**YOU MUST RUN VIPERVIZ IN THE SAME FOLDER/DIRECTORY AS MAADS-VIPER.**

VIPERviz uses websockets to connect to Web browsers over secure HTTPS connections.   Users access the visualization using standard browsers to connect to VIPERviz.  The format of the URL must be the following:

1) https://[host]:[port]/[HTML file]?topic=[Topic Name] &offset=[Offset, set to 0]&topictype=[anomaly, prediction,optimization]&secure=[1 or 0]&consumerid=[Consumer ID for the topic] &vipertoken=[Viper token]

2) For AIMS use: https://[host]:[port]/aims.html?secure=[1 or 0]&vipertoken=[copy/paste the token in ADMIN.TOK file]
