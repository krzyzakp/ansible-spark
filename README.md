ansible-spark [![Build Status](https://travis-ci.org/krzyzakp/ansible-spark.svg?branch=master)](https://travis-ci.org/krzyzakp/ansible-spark)
=========

Ansible role for installing and configuring spark master/worker services.


## Role variables
```
spark_user: spark    #User as which spark will work
spark_group: spark   #Group for spark user
spark_java_home: /usr/lib/jvm/java-8-openjdk-amd64/     #Path to java home dir
spark_version: "2.2.2"    #Spark version to install.
spark_hadoop: "hadoop2.7"    #Spark hadoop version
spark_bin_name: "spark-{{ spark_version }}-bin-{{ spark_hadoop }}.tgz"   #Spark binary name - in case package name is different from official

spark_download_mirror: "http://artfiles.org/apache.org/spark"    #Mirror to use for download
spark_download_url: "{{ spark_download_mirror }}/spark-{{ spark_version }}/{{ spark_bin_name }}"    #Full URL on mirror to download

spark_install_dir: "/opt"    #Directory for installing Spark
spark_path: "{{ spark_install_dir }}/spark-{{ spark_version }}"   #Full path where all spark files will be

spark_systemd_dir: "/etc/systemd/system/"  #Systemd directory

spark_master_enabled: !!str no  #Should spark-master be enabled?
spark_master_state: stopped    #Spark-master state on machine
spark_master_host: ""      #Spark-master host - use when different from hostname
spark_master_hosts: []     # List of spark master hosts - used by clients!
spark_master_url: "spark://{{ spark_master_hosts | join(':7077,') }}:7077"   #Spark-master url

spark_worker_enabled: !!str no   #Should spark-worker be enabled
spark_worker_state: stopped    # Spark-worker state on machine
spark_worker_cores: 4     #Ammount of Cores for spark-worker
spark_worker_memory: "2g"   #Memory for each spark-worker

spark_zookeeper_url: ""    #Zookeeper URL - used to sync all nodes 
```

## License
BSD


## Author information
Created by [krzyzakp](https://github.com/krzyzakp)
