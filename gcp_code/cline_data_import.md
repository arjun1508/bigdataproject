## install neccesary packages to download and upload data
curl -O https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-cli-385.0.0-linux-x86_64.tar.gz
sudo apt install wget

## download data from public api - can use any website here. Commented out batch uploads
wget -O taxi_2018.csv https://data.cityofchicago.org/api/views/vbsw-zws8/rows.csv?accessType=DOWNLOAD
# wget -O taxi_2019.csv https://data.cityofchicago.org/api/views/h4cq-z3dy/rows.csv?accessType=DOWNLOAD
# wget -O taxi_2020.csv https://data.cityofchicago.org/api/views/r2u4-wwk3/rows.csv?accessType=DOWNLOAD
# wget -O taxi_2021.csv https://data.cityofchicago.org/api/views/9kgb-ykyt/rows.csv?accessType=DOWNLOAD
# wget -O taxi_2022.csv https://data.cityofchicago.org/api/views/npd7-ywjz/rows.csv?accessType=DOWNLOAD

## move data to appropriate bucket
gsutil cp taxi_2018.csv gs://big_data_taxi/
gsutil cp taxi_2019.csv gs://big_data_taxi/
gsutil cp taxi_2020.csv gs://big_data_taxi/
gsutil cp taxi_2021.csv gs://big_data_taxi/
gsutil cp taxi_2022.csv gs://big_data_taxi/