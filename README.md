# XDC3DART


XDC3DART SDK with support for smart contracts, XRC20 & XRC721.

## Usage
XDC3DART is available through [pub.dev](https://pub.dev). To install
it, simply add the following command to your project:

```
dart pub add XDC3DART
```

then import modules per required 
```
Import 'package:XDC3DART/XDC3DART.dart';
```


## This SDK supports following Read & Write operations:-
```
  |    XRC20 Token: Read methods                    |   XRC20 Token: Write methods                          |
  |     ---                                         |   ---                                                 | 
  |     name()                                      |   approve(receiverAddress , amount)                   |
  |     symbol()                                    |   transfer(recipient, amount)                         |
  |     decimal()                                   |   transferFrom(sender, recipient, amount)             |
  |     totalSupply()                               |   increaseAllowance(spender, addedValue)              |
  |     balanceOf(account)                          |   decreaseAllowance(spender, subtractedValue)         |
  |     allowance(owner, spender)                   |                                                       |
  |                                                 |                                                       |
                                            
  |    XRC721 Token: Read methods                   |   XRC721 Token: Write methods                         |
  |     ----                                        |   ----                                                |
  |     name()                                      |   setApprovalForAll(operatorAddress, booleanValue)    |
  |     symbol()                                    |   approve(receiverAddress , tokenId)                  |
  |     totalSupply()                               |   transferFrom(recipient, tokenId)                    |
  |     balanceOf(owner address)                    |   safeTransferFrom(spender, tokenId)                  |
  |     ownerOf(tokenId)                            |                                                       |
  |     tokenURI(tokenId)                           |                                                       |
  |     tokenByIndex(index)                         |                                                       |
  |     tokenOfOwnerByIndex(ownerAddress,index)     |                                                       |
  |     supportInterface(interfaceId)               |                                                       |
  |     getApproved(tokenId)                        |                                                       |
  |     isApprovedForAll(ownerAddress,operator)     |                                                       |
  |                                                 |                                                       |
             
```

Create an instance of XDC3DART. This will provide you access to a set of functions interacting with the blockchain.
```
      final client = Web3Client(rpcUrl, Client(), socketConnector: () {
      return IOWebSocketChannel.connect(wsUrl).cast<String>();

```
## Example for XRC20
  name() → string Returns the name of the token.
  
```
 Future<String> name(String contractAdd) async {
    final EthereumAddress contractAddr = EthereumAddress.fromHex(contractAdd);
    final contract =
        DeployedContract(ContractAbi.fromJson(abiFile, 'XRC20'), contractAddr);
    final tokenName = contract.function('name');
    final name =
        await client.call(contract: contract, function: tokenName, params: []);
    return '$name';
  }
  ```

This example returns name of the specified address.

## Example for XRC721
 name() → string Returns the name of the token.
 ```
Future<String> name(token_address) async {
    final EthereumAddress contractAddr = EthereumAddress.fromHex(token_address);
    final contract =
        DeployedContract(ContractAbi.fromJson(abiFile, 'XRC721'), contractAddr);
    final tokenName = contract.function('name');
    final name =
        await client.call(contract: contract, function: tokenName, params: []);
    return '$name';
  }
 ```
 
   

## Author
XDCFoundation, XFLW@xinfin.org

## License
- [x] XDC3DART is available under the MIT license. See the LICENSE file for more info.
