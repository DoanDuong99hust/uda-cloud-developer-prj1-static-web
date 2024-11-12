# Create a PUBLIC bucket in the S3, and verify locally as 
aws s3api list-buckets 
# Download and unzip the udacity-starter-website.zip 
cd udacity-starter-website 

# Run terraform to deploy infra
cd terrafrom
terraform init
terrafrom validate
terraform plan
terraform apply

# Assuming the bucket name is my-bucket-202203081 and your PWD is the "udacity-starter-website" folder 
# Put a single file. 
aws s3api put-object --bucket static-web-deployment --key index.html --body index.html 
# Copy over folders from local to S3 
aws s3 cp vendor/ s3://static-web-deployment/vendor/ --recursive 
aws s3 cp css/ s3://static-web-deployment/css/ --recursive 
aws s3 cp img/ s3://static-web-deployment/img/ --recursive 

