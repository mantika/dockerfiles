#DynamodDB Logstash

This image is based on the official [logstash][1] image and adds support to DynamoDB through [DynamoDB streams](http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Tools.DynamoDBLogstash.html)

## How to use this image

The following command will get the information from a DynamoDB stream, index it in ElasticSearch so it becomes indexed by any field.

```
docker run mantika/logstash-dynamo-streams -e '
input { 
    dynamodb{endpoint => "dynamodb.us-east-1.amazonaws.com" 
    streams_endpoint => "streams.dynamodb.us-east-1.amazonaws.com" 
    view_type => "new_and_old_images" 
    aws_access_key_id => "<access_key_id>" 
    aws_secret_access_key => "<secret_key>" 
    table_name => "SourceTable"} 
} 
filter {
    dynamodb {}
}
output { 
    elasticsearch 
        { host => localhost } 
stdout { } 
}'
```

The [input][3] plugin will take care of fetching the info through the stream while the [filter][4] will decode the information and make it available to be used for the output plugins 

## License

This image is distributed under the [Apache License, Version 2.0][2].

[1]: https://hub.docker.com/_/logstash/
[2]: http://www.apache.org/licenses/LICENSE-2.0
[3]: https://github.com/awslabs/logstash-input-dynamodb
[4]: http://www.github.com/mantika/logstash-filter-dynamodb
