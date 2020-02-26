# Author
Gokul Raj S

# Supported Version
All

# Supported API Types
All

# Explanation:
This postman collection contains API Gateway REST service to create an API with IAM and LMT policy and application associated with it.

## Step 1:
Create API using file.

###### Script:
'''
let apiResponse=JSON.parse(responseBody);
pm.environment.set("apiID", apiResponse.apiResponse.api.id);
pm.environment.set("policyID", apiResponse.apiResponse.api.policies[0]);
'''

## Step 2:
Create IAM Policy Action

###### Script:
'''
let policyActionResponse=JSON.parse(responseBody);
pm.environment.set("iamPolicyActionID", policyActionResponse.policyAction.id);
'''

## Step 3:
Create Log Invocation LMT Policy Action

###### Script:
'''
let policyActionResponse=JSON.parse(responseBody);
pm.environment.set("logInvocationPolicyActionID", policyActionResponse.policyAction.id);
'''

## Step 4:
Get API policy with PolicyID. Fetch the policy from API creation response.

###### Script:
'''
let policyResponse=JSON.parse(responseBody);
pm.environment.set()
pm.environment.set("policyName",""+policyResponse.policy.names[0].value);
pm.environment.set("policyDescription",policyResponse.policy.descriptions[0].value);
    
let policyEnforcements=policyResponse.policy.policyEnforcements;
for(var i=0;i<policyEnforcements.length;i++){
    if(policyEnforcements[i].stageKey=="routing"){
        pm.environment.set("routingPolicyActionID",policyEnforcements[i].enforcements[0].enforcementObjectId);
    }
    if(policyEnforcements[i].stageKey=="transport"){
        pm.environment.set("transportPolicyActionID",policyEnforcements[i].enforcements[0].enforcementObjectId);
    }
}
'''

## Step 5:
Associate the created policy action with it.

## Step 6:
Create Application with username identifier.

###### Script:
'''
let applicatonResponse=JSON.parse(responseBody);
pm.environment.set("applicationID", applicatonResponse.id);
'''

## Step 7:
Associate created application with API.

## Step 8:
Activate the API.
