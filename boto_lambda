def lambda_handler(event, context):
    source_bucket = 'bname2000'
    destination_bucket = 'bname2001'

    s3 = boto3.client('s3')

    objects = s3.list_objects_v2(Bucket=source_bucket)

    
    for obj in objects.get('Contents', []):
        copy_source = {'Bucket': source_bucket, 'Key': obj['Key']}
        destination_key = obj['Key']  # You can modify the destination key if needed
        s3.copy_object(CopySource=copy_source, Bucket=destination_bucket, Key=destination_key,ACL='bucket-owner-full-control')

    return {
        'statusCode': 200,
        'body': 'Objects copied successfully!'
    }
