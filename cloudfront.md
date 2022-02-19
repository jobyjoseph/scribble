# Cloudfront

These are some notes and contents taken by me as part of learning Cloudfront. The content is not structured and I apologize for the same.

Amazon CloudFront is a web service that speeds up **distribution of your static and dynamic web content**, such as .html, .css, .js, and image files, to your users. CloudFront delivers your content through a worldwide network of data centers called **edge locations**.

- If the content is already in the edge location with the lowest latency, CloudFront delivers it immediately.
- If the content is not in that edge location, CloudFront retrieves it from an origin that you've defined — such as an Amazon S3 bucket, a MediaPackage channel, or an HTTP server (for example, a web server) that you have identified as the source for the definitive version of your content.

## Configure CloudFront to deliver content

1. You specify **origin servers**, like an Amazon S3 bucket or your own HTTP server, from which CloudFront gets your files which will then be distributed from CloudFront edge locations all over the world.
2. You **upload your files** to your origin servers. Your files, also known as objects, typically include web pages, images, and media files, but can be anything that can be served over HTTP.
3. You **create a CloudFront distribution**, which tells CloudFront which origin servers to get your files from when users request the files through your web site or application. At the same time, you specify details such as whether you want CloudFront to **log all requests** and whether you want the distribution to be enabled as soon as it's created.
4. CloudFront **assigns a domain name** to your new distribution.
5. CloudFront sends your distribution's configuration (but not your content) to all of its edge locations or points of presence (POPs)— collections of servers in geographically-dispersed data centers where CloudFront caches copies of your files.

Optionally, you can configure your origin server to **add headers to the files**, to indicate how long you want the files to stay in the cache in CloudFront edge locations. By default, each file stays in an edge location for **24 hours** before it expires.

## Global Edge Locations

Cloudfront serve the assets from edge locations for lower latency. [This link](https://aws.amazon.com/cloudfront/features/?whats-new-cloudfront.sort-by=item.additionalFields.postDateTime&whats-new-cloudfront.sort-order=desc#Global_Edge_Network) shows the locations of edge locations on a world map.

Here is the [IP range](https://ip-ranges.amazonaws.com/ip-ranges.json) of edge locations. The information about IP will help us to whitelist IPs in our project.

## Accessing CloudFront

We can make use of CloudFront services through:

1. AWS Management Console
2. AWS SDKs
3. Direct CloudFront APIs
4. AWS Command Line Tools
5. AWS Tools for Windows Powershell

## Restrict Direct Access to S3

To restrict access to content that you serve from Amazon S3 buckets, follow these steps:

Create a special CloudFront user called an **origin access identity (OAI)** and associate it with your distribution.

Configure your S3 bucket permissions so that CloudFront can use the OAI to access the files in your bucket and serve them to your users. Make sure that users can't use a direct URL to the S3 bucket to access a file there.

After you take these steps, users can only access your files through CloudFront, not directly from the S3 bucket.

[More details here](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/private-content-restricting-access-to-s3.html)
