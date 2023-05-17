# What is Finney?

**But first, who was Finney**

[Hal Finney](https://en.wikipedia.org/wiki/Hal_Finney_(computer_scientist)) was a computer scientist and Cypherpunk who recieved the first Bitcoin from Satoshi Nakamoto in January 2009.

```In 2004, Finney created the first reusable proof of work system before Bitcoin.[10] In January 2009, Finney was the Bitcoin network's first transaction recipient from the legendary Satoshi Nakamoto.```

This person is of signifigance because he created the blue-print. Bittensor is another take on that blue-print, only this time, it leverages both Block-chain and AI to it's advantage.
Without Finney, we wouldn't be here today - so if you want anybody to thank, I would thank him.

# Finney Prompt Subnetwork - a.k.a netuid 1

The very first subnetwork on the Finney Network -- prompt subnetworks -- is now available for mining and usage. The prompting subnetwork enables Bittensor to run many prompt neural networks such as GPT-3, GPT-4, ChatGPT, Vicuna, and others to perform **decentralized inference**. This allows users to communicate with the Validators on the network to get the output of the best performing models on the network to power their applications. 

## Testing on the prompting Subnet

Using btcli you can specify you wish to run your miner on the testnet by adding the following flags: 
```--subtensor.network finney --subtensor.chain_endpoint wss://test.finney.opentensor.ai:443.```

## Hardware Requirements

Various sources will tell you various things but I believe there is a baseline: 
## NetUID 3: 
NetUID 3 will soon be decommissioned, meaning that we will begin to see other subnets. Things that allow for multi-modality. If you are unfamiliar with the concept, this means that not only will the network offer LLMs, but ImaGens(image generators), Transcription, Voice generation - and more. The point of this network is to plug any form of generative AI into it, and then use the collective to improve and further the quality and diversity of the networks tools.

## To run a Validator on NetUID 1:

GPU machine with 24GB VRAM.
60GB of disk space is enough, though 100GB is good. 
My sources say that running an A6000 only uses 50% of resources. I suppose you could use that as a benchmark. 

NetUID 3 is CPU based and involves a lot of verification but nothing heavier. 
NetUID 1 requires running a rewarding model which requires GPU. It is gating the prompts and back propagating the responses as far as I am aware. This is more intensive therefore the GPU is required. 

Ideally, as time progresses, the models will become smaller - some models may soon run and mine on 3090s or 4090s, so it's perfectly reasonable to assume that Bittensor will soon become more accessible to people. 

The same requirements should apply to miners, but the more VRAM and RAM the better, generally speaking. It depends on the model you're serving. A6000 is generally a good baseline though! 

## Registration

Registration in the prompting network is performed the same way you have always registered, by either solving PoW or using recycle_register. Unless you have the hardware necessary to run 40x 4090s simultaneously(maybe less, maybe more idk), I would suggest:
```btcli recycle_register```

## Usage instructions
To utilize the prompt subnetwork, run the following commands in your terminal.

```bash
cd ~/.bittensor/bittensor && git pull origin text_prompting
cd ~/.bittensor/bittensor && python3 -m pip install -e .
```

All the default Servers are in the following directory within the Bittensor root directory (~/.bittensor/bittensor).

For instance, to run a `pythia` miner, use the following command:

```bash
python3 ~/.bittensor/bittensor/neurons/text/prompting/Servers/pythia/neuron.py 
```

You can still use flags as before. For example to run the `pythia` miner in the test network (Test network has subnetwork UID 91 as the prompt subnetwork):

```bash
python3 ~/.bittensor/bittensor/neurons/text/prompting/Servers/pythia/neuron.py --wallet.name prompt_Servers --wallet.hotkey prompt_miner1 --subtensor.network finney --subtensor.chain_endpoint wss://test.finney.opentensor.ai:443 --netuid 1

```

You can run the core validator by typing the following:

```bash
python3 ~/.bittensor/bittensor/neurons/text/prompting/Validators/core/neuron.py
```

