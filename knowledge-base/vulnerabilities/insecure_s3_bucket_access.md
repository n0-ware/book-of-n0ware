# Insecure S3 Bucket Access
## Description
Insecure [AWS S3 Bucket](https://aws.amazon.com/s3/) Access is a common problem facing IT Departments that do not properly secure their resources, either through negligence or lack of knowledge. An S3 bucket that is made world readable (or even writeable) can pose extraordinary risks to the organization that owns the bucket.

Assets can be hosted freely easily and very cheaply on S3, making it an attractive option for companies to use for their resources. Occasionally, IT teams will circumvent the often bureaucratic nature of corporate governance by using S3 to host assets such as PDFs and images

## Identifying Buckets
Items hosted on buckets are easy to identify through the links used to represent them on the website. The links look like:

`http://BUCKETNAME.s3.amazonaws.com/FILENAME.ext` 

or

`http://s3.amazonaws.com/BUCKETNAME/FILENAME.ext`

## Bucket Commands
If you want to list the contents of a bucket to test if it is open, you can attempt to `curl` the bucket. The IRS makes a bucket of all the tax filings of Tax-Exempt corporations that file 990s