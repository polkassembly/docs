---
title: API & Resources
category: Jekyll
layout: post
---

# Polkassembly API Documentation

This document provides information about the Polkassembly API endpoints that are available for third-party developers. All requests should include the appropriate headers for authentication and network specification.

## Base URL

The base URL for the Polkassembly API depends on the network you are targeting:

- Polkadot: `https://polkadot.polkassembly.io/`
- Kusama: `https://kusama.polkassembly.io/`
- Moonbeam: `https://moonbeam.polkassembly.io/`
- Moonriver: `https://moonriver.polkassembly.io/`

## Required Headers

All API requests require the following headers:

- `x-network`: The network you are targeting (e.g., "polkadot", "kusama", "moonbeam", "moonriver")
- `Content-Type`: `application/json`

For authenticated requests, you may also need:
- `Authorization`: `Bearer <jwt_token>`

## API Endpoints

### Posts

#### Get On-Chain Post

Retrieves information about an on-chain proposal.

**URL**: `/v1/posts/on-chain-post`

**Method**: `GET`

**Query Parameters**:
- `postId` (required): The ID of the post
- `proposalType` (required): The type of proposal (e.g., "referendums_v2", "treasury_proposals", "bounties")

**Example Request**:
```javascript
const response = await fetch(
  "https://polkadot.polkassembly.io/api/v1/posts/on-chain-post?postId=123&proposalType=referendums_v2",
  {
    headers: {
      "x-network": "polkadot"
    }
  }
);
```


### Comments

#### Get Comments by Timeline

Retrieves comments for a post organized by timeline/history.

**URL**: `/v1/posts/comments/getCommentsByTimeline`

**Method**: `POST`

**Request Body**:
```json
{
  "postId": 123,
  "proposalType": "referendums_v2"
}
```

**Example Request**:
```javascript
const response = await fetch(
  "https://polkadot.polkassembly.io/api/v1/posts/comments/getCommentsByTimeline",
  {
    method: "POST",
    headers: {
      "x-network": "polkadot",
      "Content-Type": "application/json"
    },
    body: JSON.stringify({
      postId: 123,
      proposalType: "referendums_v2"
    })
  }
);
```

### Votes

#### Get Total Votes

Retrieves the total votes for a specific proposal.

**URL**: `/v1/votes/total`

**Method**: `POST`

**Request Body**:
```json
{
  "postId": 123,
  "voteType": "referendum"
}
```

**Example Request**:
```javascript
const response = await fetch(
  "https://polkadot.polkassembly.io/api/v1/votes/total",
  {
    method: "POST",
    headers: {
      "x-network": "polkadot",
      "Content-Type": "application/json"
    },
    body: JSON.stringify({
      postId: 123,
      voteType: "referendum"
    })
  }
);
```

#### Get Aye/Nay Vote Count

Retrieves the counts of aye and nay votes for a proposal.

**URL**: `/v1/votes/ayeNayTotalCount`

**Method**: `POST`

**Request Body**:
```json
{
  "postId": 123,
  "voteType": "referendum"
}
```

**Example Request**:
```javascript
const response = await fetch(
  "https://polkadot.polkassembly.io/api/v1/votes/ayeNayTotalCount",
  {
    method: "POST",
    headers: {
      "x-network": "polkadot",
      "Content-Type": "application/json"
    },
    body: JSON.stringify({
      postId: 123,
      voteType: "referendum"
    })
  }
);
```

#### Get Votes History

Retrieves voting history for a proposal.

**URL**: `/v1/votes/history`

**Method**: `POST`

**Request Body**:
```json
{
  "postId": 123,
  "voteType": "referendum"
}
```

**Example Request**:
```javascript
const response = await fetch(
  "https://polkadot.polkassembly.io/api/v1/votes/history",
  {
    method: "POST",
    headers: {
      "x-network": "polkadot",
      "Content-Type": "application/json"
    },
    body: JSON.stringify({
      postId: 123,
      voteType: "referendum"
    })
  }
);
```

### User Data

#### Get User Activities

Retrieves activities for a specific user.

**URL**: `/v1/users/user-activities`

**Method**: `POST`

**Request Body**:
```json
{
  "address": "5GrwvaEF5zXb26Fz9rcQpDWS57CtERHpNehXCPcNoHGKutQY"
}
```

**Example Request**:
```javascript
const response = await fetch(
  "https://polkadot.polkassembly.io/api/v1/users/user-activities",
  {
    method: "POST",
    headers: {
      "x-network": "polkadot",
      "Content-Type": "application/json"
    },
    body: JSON.stringify({
      address: "5GrwvaEF5zXb26Fz9rcQpDWS57CtERHpNehXCPcNoHGKutQY"
    })
  }
);
```

#### Check Username Existence

Checks if a username is already taken.

**URL**: `/v1/users/username-exist`

**Method**: `POST`

**Request Body**:
```json
{
  "username": "exampleUser"
}
```

**Example Request**:
```javascript
const response = await fetch(
  "https://polkadot.polkassembly.io/api/v1/users/username-exist",
  {
    method: "POST",
    headers: {
      "x-network": "polkadot",
      "Content-Type": "application/json"
    },
    body: JSON.stringify({
      username: "exampleUser"
    })
  }
);
```

### Delegations

#### Get Delegation Vote Count and Power

Retrieves information about delegation votes and their voting power.

**URL**: `/v1/votes/delegationVoteCountAndPower`

**Method**: `POST`

**Request Body**:
```json
{
  "postId": 123,
  "voteType": "referendum"
}
```

**Example Request**:
```javascript
const response = await fetch(
  "https://polkadot.polkassembly.io/api/v1/votes/delegationVoteCountAndPower",
  {
    method: "POST",
    headers: {
      "x-network": "polkadot",
      "Content-Type": "application/json"
    },
    body: JSON.stringify({
      postId: 123,
      voteType: "referendum"
    })
  }
);
```

## Response Format

All API responses follow a standard format:

```json
{
  "data": {
    // The requested data
  },
  "status": 200, // HTTP status code
  "error": "" // Empty string if no error, otherwise contains error message
}
```

## Error Handling

When an error occurs, the API will return a response with an appropriate HTTP status code and an error message:

```json
{
  "error": "Error message describing what went wrong"
}
```

Common error status codes:
- `400`: Bad Request - The request was malformed or missing required parameters
- `401`: Unauthorized - Authentication is required or the provided credentials are invalid
- `403`: Forbidden - The authenticated user does not have permission to access the requested resource
- `404`: Not Found - The requested resource does not exist
- `500`: Internal Server Error - An unexpected error occurred on the server

## API Usage Limitations

Be mindful of rate limits when using the Polkassembly API. Excessive requests may lead to temporary IP blocking. For high-volume applications, please contact the Polkassembly team.

## Further Assistance

For further assistance or questions about the API, please contact the Polkassembly team through their official channels. 

**Updated API Documentation (After 16 March'23)**
[Documentation Link](https://documenter.getpostman.com/view/764953/2s93JxqLoH#181400b9-281a-44d2-91ff-93f9f6bf079e)


**Resources​**

- [Polkadot Wiki](https://wiki.polkadot.network/docs/getting-started)

- [Initial Governance Description](https://github.com/paritytech/polkadot/wiki/Governance)

- [Democracy Pallet](https://github.com/paritytech/substrate/tree/master/frame/democracy/src)

- [Governance Demo](https://www.youtube.com/watch?v=VsZuDJMmVPY&t=24734s) - Dr. Gavin Wood presents the initial governance structure for Polkadot. (Video)
