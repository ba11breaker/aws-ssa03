# 真题解析

A solution architect is designing a solution to access a catalog of `images` and provide users with the ability to `submit requests to customize iamges`. Image customization parameters will be in any request sent to an `AWS API Gateway`. The customized image will be generated `on demand`, and users will `receive a link they can click to view or download their customized image`. The solution must be `highly available` for viewing and customizing images. What is the `MOST cost-effective` solution to meet these requirements?

```
A. Use Amazon EC2 instances to manipulate the original image into the requested customization. Store the original and manipulated images in Amazon S3 Configure an Elastic Load Balancer in front of the EC2 instances.

B. Use AWS Lambda to manipulate the original image to the requested image to the requested customization. Store the original and manipulated images in `Amazon S3`. Configure an `Amazon CloudFront` distribution with the S3 bucket at the origin.

C. Use AWS Lambda to manipulate the original iamge to the requested customization. Store the original images in Amazon S3 and the manipulated images in `Amazon DynamoDB`. Configure an Elastic Load Balancer in front of the Amazon EC2 instances.

D. Use Amazon EC2 instances to manipulate the original image into the requested customizaion. Store the original images in Amazon S3 and the manipulated images in Amazon DynamoDB. Configure an Amazon CloudFront distribution with the S3 bucket as the origin.

```

## 分析

A不是最优选项，看到`AWS API Gateway`就要想到serverless,所以排除A和D。B和C中，DynamoDB是key-alue数据库，存图片限制存储400kb数据，所以不具备成本优势，优先选择B。