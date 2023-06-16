# python-wallet-creator
一个简单的Python程序，用于批量创建钱包。该代码库使用以太坊相关库来生成指定数量的钱包，并将私钥和地址保存到一个 JSON 文件中。这个代码库适用于加密货币爱好者、开发人员和研究人员，可以作为学习如何生成钱包和处理JSON文件的示例。
import os
import json
from web3 import Web3
from eth_account import Account

def create_wallets(num_wallets):
    wallets = []
    for _ in range(num_wallets):
        account = Account.create()
        private_key = account.privateKey.hex()
        address = account.address
        wallet = {
            "private_key": private_key,
            "address": address
        }
        wallets.append(wallet)
    return wallets

num_wallets = int(input("请输入要创建的钱包数量："))
wallets = create_wallets(num_wallets)

# 将钱包信息保存到文件
file_name = "wallets.json"
with open(file_name, "w") as file:
    json.dump(wallets, file, indent=4)
print(f"钱包信息已保存到文件：{file_name}")
