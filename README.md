# Learning_Services

A service to learn about Olas agents and Open Autonomy.
System requirements

    Python >=3.10
    Tendermint ==0.34.19
    IPFS node ==0.6.0
    Pip
    Poetry
    Docker Engine
    Docker Compose
    Set Docker permissions so you can run containers as non-root user

Run you own agent
Get the code

Clone this repo:

git clone git@github.com:valory-xyz/academy-learning-service-template.git

Create the virtual environment:

cd academy-learning-service
poetry shell
poetry install

Sync packages:

autonomy packages sync --update-packages

Prepare the data

Prepare a keys.json file containing wallet address and the private key for each of the four agents.

autonomy generate-key ethereum -n 4

Prepare a ethereum_private_key.txt file containing one of the private keys from keys.json. Ensure that there is no newline at the end.

Deploy a Safe on Gnosis (it's free) and set your agent addresses as signers. Set the signature threshold to 3 out of 4.

Fund your agents and Safe with a small amount of xDAI, i.e. $0.02 each.

Make a copy of the env file:

cp sample.env .env

    Fill in the required environment variables in .env. These variables are: ALL_PARTICIPANTS, GNOSIS_LEDGER_RPC, COINGECKO_API_KEY and SAFE_CONTRACT_ADDRESS. You will need to get a Coingecko free API and a Tenderly fork RPC (or alternatively an actual mainnet RPC if you want to run against the real chain).

Run the service

Check that Docker is running:

docker

Run the service:

bash run_service.sh

Look at the service logs (on another terminal):

docker logs -f learningservice_abci_0

Run a single agent

Run the agent:

bash run_agent.sh

