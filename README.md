# polkadot-custom-query
This script provides a flexible interface for executing custom queries on the Polkadot blockchain.

from substrateinterface import SubstrateInterface, Keypair

class PolkadotCustomQueryScript:
    def __init__(self, node_url, keypair):
        self.substrate = SubstrateInterface(url=node_url)
        self.keypair = keypair

    def custom_query(self, module, storage_function, params=None):
        # Execute a custom query on the Polkadot blockchain
        query_result = self.substrate.query(
            module=module,
            storage_function=storage_function,
            params=params
        )
        print(f"Custom Query Result for {module}.{storage_function} with Parameters {params}:")
        print(query_result)
        print("-" * 30)

# Example Usage
node_url = "wss://rpc.polkadot.io"
alice_keypair = Keypair.create_from_mnemonic("your_alice_mnemonic_here")

custom_query_script = PolkadotCustomQueryScript(node_url, alice_keypair)

# Execute a custom query (example: get balance for a specific account)
query_params = [alice_keypair.ss58_address]
custom_query_script.custom_query('Balances', 'freeBalance', query_params)


This script provides a flexible interface for executing custom queries on the Polkadot blockchain. Users can define modules, storage functions, and parameters to obtain specific information tailored to their needs. It serves as a versatile tool for developers looking to explore and analyze the intricacies of the Polkadot network.
