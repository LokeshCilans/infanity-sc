# Infinity Contract Check


## Problem Identification
- **Source:** (https://etherscan.io/tx/0x80f4f5553839d303c3972593fb9165bf74dba3391b32370f78567fbd16b6a41c)
- **Parameter Called:**
![upload_509da34eecc79d629f597d62d2351cf1 (1)](https://hackmd.io/_uploads/S1Fi40jJC.png)

### Cause of Failing
1. Upon calling `getCollectionInfo` for item ID 12, it was discovered that `maxMintPerTx` is set to 0.


![upload_d221ea34af5361f6fce94f38edfb1ced](https://hackmd.io/_uploads/rJReSAskR.png)


Here is the response for item ID 12.


2. In the `mintByCollectionType` function, a check ensures that the quantity does not exceed `maxMintPerTx`. As `maxMintPerTx` is 0 and a quantity of 1 is sent, the condition fails, resulting in transaction reversal.

#### Condition
- **here is the Condition.
![upload_9ee50ffc673a29cfeedb19b72228bc58](https://hackmd.io/_uploads/HJbLSCjyR.png)



## Solution

- The **maxMintPerTx** must be increased for a solution, or it must be set to 1 by using the **UpdateInfinityData** function.
