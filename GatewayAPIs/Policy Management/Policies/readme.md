# Author
Gokul Raj S

# Supported Version
10.1 and above

# Supported API Types
All

# Explanation: 
PolicyPayload.json contains the payload to create policy in API Gateway. API Gateway consist of several types of policies. 

They are
  1. SCOPE - Scope Level Policy
  2. SERVICE - API Level Policy
  3. GLOBAL - Global Policy
  4. TEMPLATE - Policy Template
  
The hierarchy of policies goes like Scope -> Service -> Global. Scope policy overrides the other exisiting policies.

We can change the policyScope with the above mentioned policies type to create the respective policy.

Before creating policy first we need to the required policy action and then associate the created policy action with the policy.

Note: One policy action must associate with one policy. Can't associate with more than one policy.
