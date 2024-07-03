
# Budget creation:
``
 aws budgets create-budget \
    --account-id $AWS_ACCOUNT_ID \
    --budget file://aws/json/budget.json \
    --notifications-with-subscribers file://aws/json/notifications-with-subscribers.json
``



# Create a Billing alarm: I created a billing alarm follwing the below steps

- 1st step is to create an SNS topic using the aws cli: 
    ```sh
    aws sns create-topic --name billing-alarm 
    ```

- 2nd step i created a subscribers using the below cli command:   
`aws sns subscribe \
    --topic-arn arn:aws:sns:eu-west-1:AWS_ACCOUNT_ID:billing-alarm \
    --protocol email \  
    --notification-endpoint unaichi.chinonso@gmail.com 
    `

- 3rd, i created an alarm using "put-metric-alarm", i copied the json configuration for the put-metric-alarm command from the this link (https://repost.aws/knowledge-center/cloudwatch-estimatedcharges-alarm):

    `aws cloudwatch put-metric-alarm --cli-input-json file://json/aws/alarm-config.json`

# How to remove sensitive information from public GitHub repository
