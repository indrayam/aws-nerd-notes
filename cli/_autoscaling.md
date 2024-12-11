# aws autoscaling

## List of Autoscaling Groups (ASG)

```bash
aws autoscaling describe-auto-scaling-groups --region us-east-2 | jq .
```


## Attach existing instances to an Autoscaling Group (ASG)

To attach an existing instance, make sure that the **desired size** of the ASG is less than the **max size**. 

For example, let's say your ASG specifications are:
- Desired size: **3**
- Min size: **1**
- Max size: **3**

With such a configuration, you will not be able to attach an existing instance to this ASG. Why? Because the ASG will always be at its max number of instances.

```bash
aws autoscaling attach-instances --instance-ids i-0fde91489baf20663 --auto-scaling-group-name play-nginx-asg
```
