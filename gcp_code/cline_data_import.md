curl -O https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-cli-385.0.0-linux-x86_64.tar.gz
sudo apt install wget
wget -O taxi_2018.csv https://data.cityofchicago.org/api/views/vbsw-zws8/rows.csv?accessType=DOWNLOAD
gsutil cp taxi_2018.csv gs://big_data_taxi/