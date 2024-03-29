
Open your  wallet.

Go to Tools -> Debug console.

Type the following RPC command, to create an address for the masternode fee:

getnewaddress

Example output

TRPLV4dXmEFMSgXg2Xu6skN9pmw8TAo4N5

Go back to your wallet overview.

Press on the toolbar button "Send".

Enter the address from the RPC command “getnewaddress” behind the text "Pay To:". (Example: TRPLV4dXmEFMSgXg2Xu6skN9pmw8TAo4N5)

Enter the following amount of coins behind the text "Amount:": 5

Press on the button "Send".

Wait until the transaction is confirmed by 6 blocks.

Go back to the console of your wallet.

Type the following RPC command, to create an address for the masternode collateral:

getnewaddress

Example output

TFi68ygQkc8h27DyeBwPykVHjF6oh8PGkH

Go back to your wallet overview.

Press on the toolbar button "Send".

Enter the address from the RPC command “getnewaddress” behind the text "Pay To:". (Example: TFi68ygQkc8h27DyeBwPykVHjF6oh8PGkH)

Enter the following amount of coins behind the text "Amount:": 5000

Press on the button "Send".

Wait until the transaction is confirmed by 15 blocks.

Go back to the console of your wallet.

Identify the transaction with the following RPC command:

masternode outputs

Example output

{
 "fdab9dff1ff9caf5d291905ad43b9f7d69775189d4d22cb085d7fedd94ea1c6a": "0"
}

Generate a BLS key pair with the the following RPC command:

bls generate

Example output

{
 "secret": "0acbf6f183d0c9b794b9bc0dba25f8a1a1eca21aa4f2e4a86ecd3120a59efb35",
 "public": "064bb1741f4707cfe3629176857c41e0d23cbe751061fe5d0d67b506db10c8f3f6f2b684c3cec8e4a128193a001d12e9"
}

Type the following RPC command, to create an address for the owner of the masternode:

getnewaddress

Example output

TWXGVYPHGA4gWcZ9Zp2qnubFVNagvorwEN

Type the following RPC command, to create an address for used for proposal voting:

getnewaddress

Example output

TSsrnbtJGYD1WmVsrsvauuwxibJyqkkqqL

Type the following RPC command, to create an address to receive the masternode reward:

getnewaddress

Example output

TEXj9AgdCh1giGmr1BXpYsngmkMkthNngD

Prepare the ProRegTx transaction by modifying the following line.

protx register_prepare fdab9dff1ff9caf5d291905ad43b9f7d69775189d4d22cb085d7fedd94ea1c6a 0 203.0.113.53:15968 TWXGVYPHGA4gWcZ9Zp2qnubFVNagvorwEN 064bb1741f4707cfe3629176857c41e0d23cbe751061fe5d0d67b506db10c8f3f6f2b684c3cec8e4a128193a001d12e9 TSsrnbtJGYD1WmVsrsvauuwxibJyqkkqqL 0 TEXj9AgdCh1giGmr1BXpYsngmkMkthNngD TRPLV4dXmEFMSgXg2Xu6skN9pmw8TAo4N5

fdab9dff1ff9caf5d291905ad43b9f7d69775189d4d22cb085d7fedd94ea1c6a - Transaction id from the RPC command “masternode outputs”.

0 - Single digit from the RPC command “masternode outputs”.

203.0.113.53:15968 - External IPv4 address of your VPS.

TWXGVYPHGA4gWcZ9Zp2qnubFVNagvorwEN - Address of the owner of the masternode.

064bb1741f4707cfe3629176857c41e0d23cbe751061fe5d0d67b506db10c8f3f6f2b684c3cec8e4a128193a001d12e9 - “public” value from the RPC command “bls generate”.

TSsrnbtJGYD1WmVsrsvauuwxibJyqkkqqL - Address used for proposal voting.

TEXj9AgdCh1giGmr1BXpYsngmkMkthNngD - Address to receive the masternode reward.

TRPLV4dXmEFMSgXg2Xu6skN9pmw8TAo4N5 - Address to where you send the masternode amount fee.

Paste the modified line into your console.

Example output

{
 "tx": "0300010001a55ee8d6ad1d5c1409a5328f4e53e80e3e7c83cf85253594141505fa64c5eeec0000000000feffffff0121dff505000000001976a9144f18fd993c0f9458fafb4985536dd358e9899a9f88ac00000000d10100000000006a1cea94ddfed785b02cd2d4895177697d9f3bd45a9091d2f5caf91fff9dabfd0000000000000000000000000000ffff88909c3714c4e172bd9c230db9cac3e446945cff2ea6720c2eca064bb1741f4707cfe3629176857c41e0d23cbe751061fe5d0d67b506db10c8f3f6f2b684c3cec8e4a128193a001d12e9b9772f1f7b0af05a67883806a4f60ddde4ecbf9e00001976a9143206f92dd6acc1a481cbb88fcadc19d0507bcb7d88ac0c5537044361500975adba10f9299f684f62a7f544e8e671638fee2c3914349f00",
 "collateralAddress": "TRPLV4dXmEFMSgXg2Xu6skN9pmw8TAo4N5",
 "signMessage": "TEXj9AgdCh1giGmr1BXpYsngmkMkthNngD|0|TWXGVYPHGA4gWcZ9Zp2qnubFVNagvorwEN|TSsrnbtJGYD1WmVsrsvauuwxibJyqkkqqL|ac19e80b02d4e8a27feb42073114070a281a2b788ba064803e8064d259b22ebc"
}


Sign the ProRegTx transaction by modifying the following line.

signmessage "TRPLV4dXmEFMSgXg2Xu6skN9pmw8TAo4N5" "TEXj9AgdCh1giGmr1BXpYsngmkMkthNngD|0|TWXGVYPHGA4gWcZ9Zp2qnubFVNagvorwEN|TSsrnbtJGYD1WmVsrsvauuwxibJyqkkqqL|ac19e80b02d4e8a27feb42073114070a281a2b788ba064803e8064d259b22ebc"

TRPLV4dXmEFMSgXg2Xu6skN9pmw8TAo4N5 - “collateralAddress” value from the RPC command “protx register_prepare”.

TEXj9AgdCh1giGmr1BXpYsngmkMkthNngD|0|TWXGVYPHGA4gWcZ9Zp2qnubFVNagvorwEN|TSsrnbtJGYD1WmVsrsvauuwxibJyqkkqqL|ac19e80b02d4e8a27feb42073114070a281a2b788ba064803e8064d259b22ebc - “signMessage” value from the RPC command “protx register_prepare”.

Paste the modified line into the console of your wallet.

Example output

H/d9tkCSzqdYh8qLL1c+KDIlrb4vtFSfdxd88XDc3U/hRZ6lMuAR8TULy7vh1YXGk6AYFFV1xyPNuEdZVMN9SdI=

Submit the ProRegTx transaction by modifying the following line.

protx register_submit 0300010001a55ee8d6ad1d5c1409a5328f4e53e80e3e7c83cf85253594141505fa64c5eeec0000000000feffffff0121dff505000000001976a9144f18fd993c0f9458fafb4985536dd358e9899a9f88ac00000000d10100000000006a1cea94ddfed785b02cd2d4895177697d9f3bd45a9091d2f5caf91fff9dabfd0000000000000000000000000000ffff88909c3714c4e172bd9c230db9cac3e446945cff2ea6720c2eca064bb1741f4707cfe3629176857c41e0d23cbe751061fe5d0d67b506db10c8f3f6f2b684c3cec8e4a128193a001d12e9b9772f1f7b0af05a67883806a4f60ddde4ecbf9e00001976a9143206f92dd6acc1a481cbb88fcadc19d0507bcb7d88ac0c5537044361500975adba10f9299f684f62a7f544e8e671638fee2c3914349f00 H/d9tkCSzqdYh8qLL1c+KDIlrb4vtFSfdxd88XDc3U/hRZ6lMuAR8TULy7vh1YXGk6AYFFV1xyPNuEdZVMN9SdI=

0300010001a55ee8d6ad1d5c1409a5328f4e53e80e3e7c83cf85253594141505fa64c5eeec0000000000feffffff0121dff505000000001976a9144f18fd993c0f9458fafb4985536dd358e9899a9f88ac00000000d10100000000006a1cea94ddfed785b02cd2d4895177697d9f3bd45a9091d2f5caf91fff9dabfd0000000000000000000000000000ffff88909c3714c4e172bd9c230db9cac3e446945cff2ea6720c2eca064bb1741f4707cfe3629176857c41e0d23cbe751061fe5d0d67b506db10c8f3f6f2b684c3cec8e4a128193a001d12e9b9772f1f7b0af05a67883806a4f60ddde4ecbf9e00001976a9143206f92dd6acc1a481cbb88fcadc19d0507bcb7d88ac0c5537044361500975adba10f9299f684f62a7f544e8e671638fee2c3914349f00 - “tx” value from the RPC command “protx register_prepare”.

H/d9tkCSzqdYh8qLL1c+KDIlrb4vtFSfdxd88XDc3U/hRZ6lMuAR8TULy7vh1YXGk6AYFFV1xyPNuEdZVMN9SdI= - Output from the RPC command “signmessage”.

Paste the modified line into the console of your wallet.

Example output

7da2e1187202a1a497beca05e0e53a6e4df0dc06046f72fbf8b61c942db2982a


Open putty and connect using SSH with your Ubuntu server.

Update your Ubuntu server with the following command:

sudo apt-get update && sudo apt-get upgrade -y

Type the following command to go back to your home directory:

cd $HOME

Download the Linux daemon for your wallet with the following command:

wget "https://github.com/Elevenchain/wallet/files/14231404/elevenchain-daemon-linux.tar.gz" -O elevenchain-daemon-linux.tar.gz

Extract the tar file with the following command:

tar -xzvf elevenchain-daemon-linux.tar.gz

Download the Linux tools for your wallet with the following command:

wget "https://github.com/Elevenchain/wallet/files/14231405/elevenchain-qt-linux.tar.gz" -O elevenchain-qt-linux.tar.gz

Extract the tar file with the following command:

tar -xzvf elevenchain-qt-linux.tar.gz

Type the following command to install the daemon and tools for your wallet:

sudo mv elevenchaind elevenchain-cli elevenchain-tx /usr/bin/

Create the data directory for your coin with the following command:

mkdir $HOME/.elevenchain

Open nano.

nano $HOME/.elevenchain/elevenchain.conf -t

Paste the following into nano.

rpcuser=rpc_elevenchain
rpcpassword=dR2oBQ3K1zYMZQtJFZeAerhWxaJ5Lqeq9J2
rpcbind=127.0.0.1
rpcallowip=127.0.0.1
listen=1
server=1
daemon=1
maxconnections=125
masternode=1
masternodeblsprivkey=0acbf6f183d0c9b794b9bc0dba25f8a1a1eca21aa4f2e4a86ecd3120a59efb35
externalip=203.0.113.53

203.0.113.53 - External IPv4 address of your VPS.

0acbf6f183d0c9b794b9bc0dba25f8a1a1eca21aa4f2e4a86ecd3120a59efb35 - “secret” value from the RPC command “bls generate”.

Save the file with the keyboard shortcut ctrl + x.

Type the following command to start your masternode:

elevenchaind