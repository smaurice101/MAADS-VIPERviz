# MAADS-VIPERviz

Visualize streaming insights over conventional web browers using HTTPS with websockets.

MAADS-VIPERviz is visualization technology to visualize streaming results from Kafka.  Specifically, HPDE will apply machine learning to streaming data and store results in Kafka for:
1)	Predictive Analytics:	Users can visualize these results by calling the file: **_Prediction.HTML_**
2)	Prescriptive Analytics or Optimization:	Users can visualize these results by calling the file: **_Optimization.HTML_**
3)	Anomaly Detection using unsupervised learning: Users can visualize these results by calling the file: **_Anomaly.HTML_**
4) Generic Topics with raw data can be visualized from a Kafka topic or topics. The data should have been produced by viperproducetotopic (in MAADS TML python libray or REST).  Call the html file **generictopics.HTML_**
5) Algorithms and Insights Management (AiMS): **_Aims.html_**

**INSTRUCTIONS:**
1) START: [viperviz binary] [host] [port]
2) Copy the contents of VIEWS.ZIP to the folder **_viperviz/vews_** *in the same directory as VIPER.*
3) You must have server and client certificates in the same folder as Viperviz named: client.cer.pem and client.key.pem.  Examples are provided in the ZIP files to get you started but you should have official certificates for HTTPS connections.

Viperviz will listen on [port] for HTTP and [port]+1 on HTTPS connection.  For example, if you run viperviz on port 8000, it will accept HTTP connections on port 8000, and HTTPS connections on port 8001. For **On-Prem** you may need to use HTTP.

**YOU MUST RUN VIPERVIZ IN THE SAME FOLDER/DIRECTORY AS MAADS-VIPER.**

VIPERviz uses websockets to connect to Web browsers over secure HTTPS connections.   Users access the visualization using standard browsers to connect to VIPERviz.  The format of the URL must be the following:

**1) Streaming Insights:** https://[host]:[port]/[HTML file]?topic=[Topic Name] &offset=[Offset, set to 0]&rollbackoffset=[number of offsets to rollback the data stream]&topictype=[anomaly, prediction,optimization,generic]&secure=[1 or 0]&append=[1=append all data to the web table, 0=do not append]&consumerid=[Consumer ID for the topic]&groupid=[Group id to consume parallel messages]&vipertoken=[copy/paste the token in ADMIN.TOK file]

**_NOTE_**: For topictype=generic, to visualize multiple topics, separate them by a comma in the **topic** key.  If using **HTTP**, make sure to set **secure=0** in the URL, if using HTTPS then set **secure=1** in the URL. 

**2) For AIMS use:** https://[host]:[port]/aims.html?secure=[1 or 0]&vipertoken=[copy/paste the token in ADMIN.TOK file]

**NOTES:**
1) If you are visualizing big data, then set append=0, offset=-1, and choose a rollbackoffset.  For example, if offset=-1, append=0 and rollbackoffset=100, then you will only see that last 100 entries without consuming too much memory in your web browser. 

2) rollbackoffset works when offset=-1 otherwise it is ignored.

3) if you want to do parallel consuming of insights then use Kafka's consumer group. For example, if you have 100 people who want to consume insights from 1 topic - then create a topic with 100 partitions, and use the group id.  This way, each individual will receive insights **at the same time**.
