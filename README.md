# todo_api_lambda
## introduction

This is a deployment for todo app with aws lambda and aws api gateway setup

## CREATE

```bash==
npx serverless create --template aws-nodejs --path $folder_name
```

## EndPoint
| EndPoint                                                                       | Function    | HTTP Method | Request Body                       |
|:------------------------------------------------------------------------------ |:----------- |:-----------:|:---------------------------------- |
| https://2q3xmaw2sg.execute-api.ap-northeast-2.amazonaws.com/dev/post           | createPost  |    POST     | {"title":"post 1","body":"Test 1"} |
| https://2q3xmaw2sg.execute-api.ap-northeast-2.amazonaws.com/dev/posts          | getAllPosts |     GET     |                                    |
| https://2q3xmaw2sg.execute-api.ap-northeast-2.amazonaws.com/dev/posts/{number} | getPosts    |     GET     |                                    |
| https://2q3xmaw2sg.execute-api.ap-northeast-2.amazonaws.com/dev/post/{id}      | getPost     |     GET     |                                    |
| https://2q3xmaw2sg.execute-api.ap-northeast-2.amazonaws.com/dev/post/{id}      | updatePost  |     PUT     |               {"title":"hi","body":"who are u"}|
| https://2q3xmaw2sg.execute-api.ap-northeast-2.amazonaws.com/dev/post/{id}      | updatePost  |   DELETE    |                                    |

## updatePost api
```javascript=
request method: POST
request uri: 'https://2q3xmaw2sg.execute-api.ap-northeast-2.amazonaws.com/dev/post/45ad0dc0-ecd5-4535-b55d-d55ce9cefb12'
request header: {
    'Content-Type': 'application/json',
}
resquest body: {
    title:"hi",
    body:"who r u"
}
// track time with access Token not expired
response header: 200 OK
response body: {
    createdAt: "2021-04-06T09:06:50.603Z",
    id: "45ad0dc0-ecd5-4535-b55d-d55ce9cefb12",
    userId: 1,
    body: "who r u",
    title: "hi"
}

// failed due to wrong param
response header: 400 Bad Request
response body: {
    message: "ExpressionAttributeValues must not be empty",
    code: "ValidationException",
    time: "2021-04-06T09:34:21.965Z",
    requestId: "RGSS357JBUR62DNSSEMAQPV6NJVV4KQNSO5AEMVJF66Q9ASUAAJG",
    statusCode: 400,
    retryable: false,
    retryDelay: 1.904886204668621
}

## How to Test offline
run with serverless-offline
```bash==
sls offline
```
[serverless-offline](https://www.serverless.com/plugins/serverless-offline)
