OPTIMIZATING COST BY REMOVING UNUSED EBS SNAPSHOTS

Prerequisites:
  EC2 instance,
  Lambda function,
  EventBridge

Implementation:
  1. Launch an EC2 insatnce. By default volume will be created.
     Create snapshot for the created volume that is attached to your created EC2 instance.
  2. Create a lambda function and choose runtime as python.
     Go to permissions to attach policy to communicate with EC2 instance.
       Role (open in new tab) -> create policies
         DescribeSnapshot
         DescribeInsance
         DescribeVolume
         DeleteSnapshot 
     and deploy the code ebs_stale_snapshosts.py
  3. Create a Rule in EventBridge and schedule the trigger to test Lambda function
  4. Deploy, Test and check if the snapshot is deleted on EC2 dashboard.
  5. Terminate the created EC2 instance.
  6. Test and check if the snapshot is deleted on EC2 dashboard. (SUCCESSFULLY SNAPSHOT NEEDS TO BE DELETED!!!)
