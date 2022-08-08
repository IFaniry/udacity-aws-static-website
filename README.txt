Deploy Static Website on AWS

In this project, I deploy a static website to AWS using S3, CloudFront, and IAM. The website is accessible via the following links:

http://my-546405167418-travel-blog.s3-website-us-east-1.amazonaws.com
https://d1ecgkiuab5n47.cloudfront.net

I upload the following assets to my S3 bucket "my-546405167418-travel-blog" to serve the website:

- index.html - The Index document for the website.
- /img - The background image file for the website.
- /vendor - Bootssrap CSS framework, Font, and JavaScript libraries needed for the website to function.
- /css - CSS files for the website.

These are the commands I used to upload the above files to S3 using my custom IAM User:

aws s3api put-object --bucket my-546405167418-travel-blog --key index.html --body index.html --content-type text/html --profile udacity_admin
aws s3 cp vendor/ s3://my-546405167418-travel-blog/vendor/ --recursive --profile udacity_admin
aws s3 cp css/ s3://my-546405167418-travel-blog/css/ --recursive --profile udacity_admin
aws s3 cp img/ s3://my-546405167418-travel-blog/img/ --recursive --profile udacity_admin

In the screenshots folder, I include the images of the following steps:

- creating the public S3 bucket
- allowing read permissions in the S3 bucket
- filling the S3 bucket with the website's html, css and js files
- configuring the S3 bucket for Web hosting and setting index.html as both the index and error page
- setting the origin of the Cloudfront Distribution to the custom S3 Web hosting domain name
- setting Cloudfront's default object to index.html
- viewing the deployed site in the Web browser
