# API Test CLI - Executing a simple test definition file with apic toolkit

#### Create a test definition file

[sample-api-test-definition.yaml](./sample-api-test-definition.yaml)

#### To execute tests, run

```
apic test ./sample-api-test-definition.yaml
```

#### Result

```
 -- sample-api-test-definition.yaml --
2023/12/13 17:28:49 [tests:INFO] Replace the Variables with Configuration Values If it Exists
************************************************************************
2023/12/13 17:28:49 [tests:INFO] Configuration within the YAML File : 
************************************************************************
2023/12/13 17:28:49 [tests:INFO] Checking if there is any variable in each field in each step
        ➡️ : [sample-api-test-definition.yaml:0] get request made to https://api.eu-west-a.apiconnect.ibmappdomain.cloud/demo/sandbox/order/ABC123?
        ✅︎: [sample-api-test-definition.yaml:0] request https://api.eu-west-a.apiconnect.ibmappdomain.cloud/demo/sandbox/order/ABC123
        ✅︎: [sample-api-test-definition.yaml:1] payload_response_statusCode equals 200
        ✅︎: [sample-api-test-definition.yaml:2] payload_response_header_Content-Type equals application/json
        ✅︎: [sample-api-test-definition.yaml:3] payload_response_header_Content-Type is in [application/json application/swagger+yaml]
        ✅︎: [sample-api-test-definition.yaml:4] payload_response_header_Content-Type contains app
        ✅︎: [sample-api-test-definition.yaml:5] payload_response_header_Content-Type matches ^[a-z]+/json
        ✅︎: [sample-api-test-definition.yaml:6] payload exists
        ✅︎: [sample-api-test-definition.yaml:7] payload.tracking_reference is string
        ✅︎: [sample-api-test-definition.yaml:8] payload.shipped_at exists
        ✅︎: [sample-api-test-definition.yaml:9] payload.status exists
        ✅︎: [sample-api-test-definition.yaml:10] payload.created_at exists

```