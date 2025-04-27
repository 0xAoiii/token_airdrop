# Solana Token Airdrop Script

A simple Python script to evenly airdrop your Solana token to a list of wallet addresses using the spl-token CLI.

# Requirements:

- Python 3.8+
- Solana CLI installed
- SPL Token CLI installed
- Solana wallet with sufficient SOL for transaction fees

# Setup:

1. Clone this repository:
   `git clone https://github.com/0xAoiii/token_airdrop
cd token_airdrop`
2. Prepare your wallet_addresses.csv file:

Instead of manually adding wallet addresses, use the Twitter Scraper tool to extract wallet addresses directly from Twitter comments.

3. Clone it here:

`git clone https://github.com/0xAoiii/twitter_scraper`

The Twitter Scraper will generate a wallet_addresses.csv file with the correct format:

`wallet_address
WalletAddress1
WalletAddress2
WalletAddress3
...`

Move the generated wallet_addresses.csv into the token_airdrop directory (the same folder as token_airdrop.py).

# Edit token_airdrop.py

Replace YOUR_TOKEN_MINT_ADDRESS with your actual token mint address.

Adjust the total token amount if different from 750 million tokens. (Default setup distributes 750M tokens evenly.)

# Run the Script

Inside the token_airdrop directory, run:

`python token_airdrop.py`

Tokens will be evenly sent to all listed wallet addresses.

# Notes

Be cautious with your funding! Each transfer costs a small amount of SOL.

Always test the airdrop with a few addresses first to verify everything works before sending to a large list.
