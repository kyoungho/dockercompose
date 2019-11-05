# RTI Shapes demo with TIG

Running TIG (Telegraf, InfluxDB, and Garafana) for [RTI Shapes demo](https://www.rti.com/free-trial/shapes-demo) using [docker-compose](https://docs.docker.com/compose).
This is for demonstrating [Telegraf plugin for RTI Connext DDS](https://www.rti.com/developers/rti-labs/telegraf-plugin-for-connext-dds). 

## Usage

Run Docker images:
  
    docker-compose up -d
    
After running the Docker images, you should run RTI Shapes demo and create publishers. 

The baseline QoS setting used by the DataReaders in Telegraf is `Generic.KeepLastReliable`. 
The `Square` DataReader uses the default QoS settings. 
The `Circle` DataReader uses the default QoS settings. It also defines a content-based filter (`x > 100`), so it will receive data only the x coordinate is higher than 100. 
The `Triangle` DataReader uses `TRANSIENT_LOCAL_DURABILITY_QOS` and `KEEP_ALL_HISTORY_QOS`. So it will receive all historical data from a DataWriter. 
