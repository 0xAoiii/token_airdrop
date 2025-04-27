import subprocess
import csv
import sys

# Config
TOKEN_MINT_ADDRESS = "YOUR_TOKEN_MINT_ADDRESS"  # Replace with your token mint address
WALLET_CSV_PATH = "wallet_addresses.csv"        # Path to your CSV with Solana wallet addresses
TOTAL_TOKENS = 750_000_000_000_000_000           # 750M tokens (in base units for 9 decimals)

def load_wallets(csv_path):
    wallets = set()
    try:
        with open(csv_path, newline='') as csvfile:
            reader = csv.DictReader(csvfile)
            for row in reader:
                wallet = row.get('wallet_address')
                if wallet:
                    wallets.add(wallet)
    except FileNotFoundError:
        print(f"Error: {csv_path} not found.")
        sys.exit(1)
    return list(wallets)

def airdrop_tokens(wallets, tokens_per_wallet):
    for idx, wallet in enumerate(wallets, 1):
        print(f"[{idx}/{len(wallets)}] Airdropping {tokens_per_wallet} tokens to {wallet}")
        subprocess.run([
            "spl-token", "transfer", TOKEN_MINT_ADDRESS,
            str(tokens_per_wallet), wallet, "--fund-recipient"
        ])

if __name__ == "__main__":
    wallets = load_wallets(WALLET_CSV_PATH)
    if not wallets:
        print("No wallet addresses found! Exiting.")
        exit(1)

    tokens_per_wallet = TOTAL_TOKENS // len(wallets)
    print(f"Loaded {len(wallets)} unique wallets.")
    print(f"Each wallet will receive {tokens_per_wallet} tokens.")

    airdrop_tokens(wallets, tokens_per_wallet)
