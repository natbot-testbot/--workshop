# natbot-testbot Workshop

![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)
![Node.js](https://img.shields.io/badge/Node.js-20.x-brightgreen)
![TypeScript](https://img.shields.io/badge/TypeScript-4.x-blue)

## Table of Contents

- [Project Purpose and Features](#project-purpose-and-features)
- [Installation](#installation)
- [Usage](#usage)
  - [Playing Chess](#playing-chess)
  - [AI Chess Assistant](#ai-chess-assistant)
  - [Bounty Payout Process](#bounty-payout-process)
- [Contribution Guidelines](#contribution-guidelines)
- [License](#license)
- [Contact](#contact)

## Project Purpose and Features

**natbot-testbot Workshop** is an interactive GitHub-based chess platform that allows contributors to play chess by submitting their moves through pull requests (PRs). By contributing valid moves, participants can earn SOL bounties as rewards for their contributions. The project integrates with Solana for secure and transparent bounty payouts and leverages AI to assist in analyzing and suggesting moves.

### Key Features

- **Play Chess via Pull Requests:** Submit your chess moves by creating PRs with your next move and your Solana wallet address.
- **Earn SOL Bounties:** Receive SOL rewards for accepted moves, incentivizing active participation.
- **Automated Bounty Management:** Bounties are managed through structured YAML files ensuring transparency and fairness.
- **AI Assistance:** Utilize an AI Chess Assistant powered by OpenAI to analyze games and suggest optimal moves.
- **Game Validation:** Automated workflows validate the integrity of chess games added or modified in the repository.
- **Continuous Integration:** GitHub Actions automate processes like bounty payouts and game validations upon PR merges.

## Installation

To set up the **natbot-testbot Workshop** locally, follow these steps:

### Prerequisites

- **Node.js**: Ensure you have Node.js version 20.x installed. [Download Node.js](https://nodejs.org/)
- **pnpm**: This project uses pnpm as the package manager. Install it globally if you haven't:
  ```bash
  npm install -g pnpm
  ```
- **Solana Wallet**: You need a Solana wallet with SOL to fund bounties. [Create a Solana Wallet](https://solana.com/)

### Steps

1. **Clone the Repository**
   ```bash
   git clone https://github.com/natbot-testbot/--workshop.git
   cd --workshop
   ```

2. **Install Dependencies**
   ```bash
   pnpm install
   ```

3. **Configure Environment Variables**

   Create a `.env` file in the root directory based on the provided `.env.example`:
   ```bash
   cp .env.example .env
   ```

   Populate the `.env` file with your Solana private key and RPC URL:
   ```
   SOLANA_PRIVATE_KEY=your_sol_private_key
   SOLANA_RPC_URL=https://api.mainnet-beta.solana.com
   OPENAI_API_KEY=your_openai_api_key
   ```

   > **Note:** Never commit your `.env` file or expose your private keys.

4. **Build the Project**
   ```bash
   pnpm build
   ```

## Usage

### Playing Chess

Engage in a game of chess by following these simple steps:

1. **Submit a Pull Request (PR) with Your Move**

   - Fork the repository and clone it to your local machine.
   - Navigate to the `chess/games` directory and locate the latest game PGN file.
   - Analyze the current board state and decide your next move.
   - Update the PGN file with your move following SAN (Standard Algebraic Notation) format.

2. **Include Your Solana Wallet Address**

   - In your PR description or commit message, include your Solana wallet address to receive the bounty if your move is accepted.

3. **Submit the PR**

   - Once submitted, the project maintainers will review your move.
   - If your move is valid and strengthens your position, it will be merged, and you'll receive SOL as a bounty.

### AI Chess Assistant

Leverage the AI Chess Assistant to analyze games and get move suggestions.

**Running the AI Assistant:**

```bash
pnpm ts-node chess/scripts/aiChessAssistant.ts path/to/game.pgn
```

**Example:**

```bash
pnpm ts-node chess/scripts/aiChessAssistant.ts chess/games/game_20240715.pgn
```

This script will analyze the specified game and suggest the next optimal move.

### Bounty Payout Process

Bounties are managed through a transparent and fair process:

1. **Bounty Creation**

   - Bounties are defined in YAML files located in the `.bounties` directory.
   - Each YAML file corresponds to a specific PR and specifies the task, reward amount, and criteria for completion.

2. **Task Completion**

   - Contributors work on the tasks by submitting PRs with their chess moves.
   - After making a move, the corresponding bounty YAML file is created or updated.

3. **Review and Approval**

   - Project maintainers review the submitted move.
   - If the move meets the criteria, the PR is merged, and the bounty is approved.

4. **Payment**

   - Upon approval, the `payBounty.ts` script is triggered via GitHub Actions.
   - The script processes the bounty payment using the Solana network.
   - The transaction hash is recorded in the respective YAML file for transparency.

5. **Record Keeping**

   - All bounty transactions and game states are recorded within the repository for future reference.

## Contribution Guidelines

We welcome contributions from the community! To ensure a smooth collaboration, please follow these guidelines:

### How to Contribute

1. **Fork the Repository**

   Click the "Fork" button on the [GitHub repository](https://github.com/natbot-testbot/--workshop) to create your own copy.

2. **Clone Your Fork**

   ```bash
   git clone https://github.com/your-username/--workshop.git
   cd --workshop
   ```

3. **Create a New Branch**

   ```bash
   git checkout -b feature/your-feature-name
   ```

4. **Make Your Changes**

   - **Playing Chess:** Submit your chess moves by creating PRs as described in the [Usage](#usage) section.
   - **Enhancements:** Add new features, improve scripts, or enhance the AI assistant.

5. **Commit Your Changes**

   ```bash
   git commit -m "Add feature: your feature description"
   ```

6. **Push to Your Fork**

   ```bash
   git push origin feature/your-feature-name
   ```

7. **Open a Pull Request**

   - Navigate to your fork on GitHub.
   - Click "Compare & pull request" and submit your PR following the template.

### Code Standards

- **Language:** TypeScript
- **Formatting:** Ensure code adheres to the project's [Prettier](https://prettier.io/) configuration.
  ```bash
  pnpm run lint:fix
  ```
- **Typing:** Maintain strict typing and avoid using `any` where possible.

### Testing

- Add or update tests in the `tests/` directory when modifying existing functionalities or adding new features.
- Run tests locally before submitting a PR:
  ```bash
  pnpm test
  ```

### Documentation

- Update the README.md and other relevant documentation to reflect your changes.
- Ensure clear and concise commit messages.

### Reporting Issues

- Open an issue on GitHub to report bugs or suggest features.
- Provide detailed descriptions and steps to reproduce when reporting bugs.

## License

This project is licensed under the [Apache License 2.0](LICENSE).

## Contact

For any queries or support, please reach out via [GitHub Issues](https://github.com/natbot-testbot/--workshop/issues) or contact the maintainers directly.

---

*Happy Chess Playing! 🤖♟️*