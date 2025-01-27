---
title: API & Resources
category: Jekyll
layout: post
---

# 🤖 AI Chatbot

You can talk to polkassembly using Chat GPT bot

[LINK](https://docsbot.ai/chat/X6zGLB8jx6moWVb6L5S9/D7XT9ksDuTZCvdf99KSW)

# 🤝 Integrating with Polkassembly

Kickstart your parachain's governance journey today!

**Requirements**

- RPC Endpoint

- URL for archive node

- Token

- Symbol

- Token Decimals

- Website

- Social Links

- Contact info -> Telegram ID would be perfect!

Please shoot a mail at hello@polkassembly.io with the following details and we will take it from there. Cheers!

# ⚙️ API Documentation

The power of open source

**Updated API Documentation (After 16 March'23)**
[Documentation Link](https://documenter.getpostman.com/view/764953/2s93JxqLoH#181400b9-281a-44d2-91ff-93f9f6bf079e)

**Archived API Documentation (Before 16 March'23)**

**API ENDPOINT**

Chain and GraphQL Endpoints

| **Chain**      | **GraphQL Endpoint**                                                                                           |
| -------------- | -------------------------------------------------------------------------------------------------------------- |
| kusama         | [https://kusama.polkassembly.io/v1/graphql](https://kusama.polkassembly.io/v1/graphql)                         |
| polkadot       | [https://polkadot.polkassembly.io/v1/graphql](https://polkadot.polkassembly.io/v1/graphql)                     |
| moonbase       | [https://api.moonbase.polkassembly.network/v1/graphql](https://api.moonbase.polkassembly.network/v1/graphql)   |
| moonbeam       | [https://api.moonbeam.polkassembly.network/v1/graphql](https://api.moonbeam.polkassembly.network/v1/graphql)   |
| moonriver      | [https://api.moonriver.polkassembly.network/v1/graphql](https://api.moonriver.polkassembly.network/v1/graphql) |
| other networks | [https://polkassembly-hasura.herokuapp.com/graphql](https://polkassembly-hasura.herokuapp.com/graphql)         |

**Proposal Post**

# 🙏 Resources and Reference

**Fetch proposal title and description:**

**Graphql Request:**

query {
posts(where: {onchain_link: {onchain_proposal_id: {\_eq: 113}}}) {
title
content
onchain_link {
proposer_address
}
comments {
content
created_at
author {
username
}
replies {
content
author {
username
}
}
}
}
}

Grateful for all the help!

**Resources​**

- [Polkadot Wiki](https://wiki.polkadot.network/docs/getting-started)

- [Initial Governance Description](https://github.com/paritytech/polkadot/wiki/Governance)

- [Democracy Pallet](https://github.com/paritytech/substrate/tree/master/frame/democracy/src)

- [Governance Demo](https://www.youtube.com/watch?v=VsZuDJMmVPY&t=24734s) - Dr. Gavin Wood presents the initial governance structure for Polkadot. (Video)
