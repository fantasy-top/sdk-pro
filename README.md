# Fantasy SDK Pro

Fantasy SDK Pro is a powerful TypeScript/JavaScript client for interacting with the Fantasy API. It provides a simple and intuitive interface to access various endpoints and manage fantasy-related data.

- [Installation](#installation)
- [Usage](#usage)
- [API Reference](#api-reference)
  - [CardApi](#cardapi)
  - [HeroApi](#heroapi)
  - [PlayerApi](#playerapi)
  - [TacticsApi](#tacticsapi)
  - [VotingApi](#votingapi)
- [Issue Requirements](#issue-requirements)

## Installation

Create a .npmrc to setup the registry for npm:

```
@fantasy-top:registry=https://npm.pkg.github.com
//npm.pkg.github.com/:_authToken=${GITHUB_TOKEN}
```

Create a token to read packages on Github:

`Click Your Avatar > Settings > Developer Settings > Personal access tokens > Tokens (classic) > create a new one with "read:packages"`

Install the package using npm:

`npm install @fantasy-top/sdk-pro`

## Usage
```ts
import { Client, Configuration } from '@fantasy-top/sdk-pro'

const config = new Configuration({
  basePath: process.env.API_URL, // 'https://api-v2.fantasy.top'
  apiKey: process.env.API_KEY, // 'can be obtained from https://fantasy.top/developer'
})

export const api = Client.getInstance(config)
```

```ts
const votingConfigs = await api.voting.getConfigs({
    only_visible: true,
    pagination: {
        page: 1,
        limit: 10
    }
})
```

**You can find an example with NextJS [here](https://github.com/fantasy-top/pro-example)**

## API Reference

The Fantasy SDK Pro provides access to various API endpoints through different API spaces. Here's an overview of the available API spaces and their methods:

### CardApi

- `findAllCards(page?: number, limit?: number): Promise<PaginatedCardResult>`
  - Retrieves a paginated list of all cards.

- `getCardById(id: string): Promise<Card>`
  - Fetches a specific card by its ID.

- `getCardsByPlayerId(playerId: string): Promise<Array<Card>>`
  - Retrieves all cards associated with a specific player.

- `getHeroSupply(heroId: string): Promise<HeroSupply>`
  - Gets the supply information for a specific hero.

### HeroApi

- `getAllHeroes(): Promise<Array<Hero>>`
  - Retrieves a list of all heroes.

- `getHeroesByHandleOrName(handleOrName: string): Promise<Array<Hero>>`
  - Searches for heroes by their handle or name.

- `getHeroesByIds(ids: Array<string>): Promise<Array<Hero>>`
  - Fetches multiple heroes by their IDs.

### PlayerApi

- `findPlayersBySearch(search: string): Promise<Array<Player>>`
  - Searches for players based on a search query.

- `getAllPlayersWithPagination(page?: number, limit?: number): Promise<PaginatedPlayerResult>`
  - Retrieves a paginated list of all players.

### TacticsApi

- `countEntriesByPlayerId(playerId: string): Promise<number>`
  - Counts the number of tactic entries for a specific player.

- `countTicketsByPlayerId(playerId: string): Promise<number>`
  - Counts the number of tickets for a specific player.

- `get(query?: GetTacticsQueryDTO): Promise<PaginatedTacticsResult>`
  - Retrieves a paginated list of tactics based on the provided query.

- `getById(id: string, query?: GetTacticsQueryDTO): Promise<Tactics>`
  - Fetches a specific tactic by its ID.

- `getHeroScoresByTacticId(tacticId: string, query?: GetHeroScoreQueryDTO): Promise<PaginatedTacticsHeroScoreResult>`
  - Retrieves hero scores for a specific tactic.

- `getTotalGains(playerId: string): Promise<GetTotalTicketsGainsResponseDTO>`
  - Calculates the total gains for a specific player.

### VotingApi

- `getConfigs(query?: GetVoteConfigQueryDTO): Promise<PaginatedVoteConfigResult>`
  - Retrieves a paginated list of voting configurations.

- `getVotesByHero(voteConfigId: string): Promise<Array<HeroWithVotesCount>>`
  - Fetches the vote counts for heroes in a specific voting configuration.


**For more details, please refer to the [API Swagger](https://api-v2.fantasy.top).**

*Feel free to explore the code and contribute to the SDK for any improvements or additional features.*

*Feel free to create issues, never add a pull request since the SDK it's auto-generated by openapi-generator.*


## Issue requirements

### How to Make an Issue Request for the Pro SDK

1. Check for Existing Issues
Before creating a new issue, ensure that a similar issue does not already exist. Search through the existing issues in the repository to avoid duplicates.

2. Define the Endpoint Clearly
Provide a clear and concise definition of the endpoint you are requesting. Include the following details:
- Endpoint URL: Specify the URL path for the endpoint.
- HTTP Method: Indicate whether it is a GET, POST, PUT, DELETE, etc.
- Purpose: Briefly describe the purpose of the endpoint.

3. Specify Data Requirements
- Clearly outline the data requirements for the endpoint. Include:
- Request Parameters: List any query parameters, path parameters, or body data required.
- Response Data: Describe the expected structure and content of the response.
