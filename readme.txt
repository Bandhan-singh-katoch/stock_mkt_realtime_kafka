# Tools used:
Kafka, ec2, cloud9 ide, jupyter notebook, s3, aws glue crawler, athena(for quering) 

# Install kafka
wget https://archive.apache.org/dist/kafka/3.3.2/kafka-3.3.2-src.tgz
tar -xvf kafka-3.3.2-src.tgz

# Start Zoo-keeper:
bin/zookeeper-server-start.sh config/zookeeper.properties

# Start Kafka-server:
export KAFKA_HEAP_OPTS="-Xmx256M -Xms128M"
bin/kafka-server-start.sh config/server.properties

# Create the topic: 
bin/kafka-topics.sh --create --topic my_first_topic --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1

# Start Producer:
bin/kafka-console-producer.sh --topic my_first_topic --bootstrap-server localhost:9092 

# Start Consumer:
bin/kafka-console-consumer.sh --topic my_first_topic --bootstrap-server localhost:9092

# Install Jupyter:
pip3 install jupyter
jupyter notebook --generate-config
nano ~/.jupyter/jupyter_notebook_config.py
paste these in file:
  c.NotebookApp.ip = '0.0.0.0'
  c.NotebookApp.port = 8888
  c.NotebookApp.open_browser = False
  c.NotebookApp.notebook_dir = '/home/ubuntu/environment'
jupyter notebook password

# Then go to security of ec2 and add rules:-
type: custom tcp
port : 8888
source : my ip

jupyter notebook

then copy public dns and paste on browser with 8888

# Topics list
kafka-topics.sh --bootstrap-server localhost:9092 --list
