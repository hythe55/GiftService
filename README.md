# GiftService
Adds support for users to gift gamepasses and products to other users. Automatically saves when a user purchases a gamepass or is gifted one to avoid repeat purchases.

## Important Information
All `MarketplaceService:UserOwnsGamePassAsync()` calls should be replaced with `GiftService:UserOwnsGamePassAsync()`. `GiftService:UserOwnsGamePassAsync()` will return true if the player either owns the gamepass or has been gifted the gamepass using GiftService. See `Methods > UserOwnsGamePassAsync` for more information

## Methods
### PromptProductGift
Prompts the product gifting GUI to the given `Player`.

#### Parameters
| Parameter | Type | Description | 
| ----------- | ----------- | ----------- |
| `player` | `Player` | The `Player` to prompt the product gift gui to. |
| `productId` | `number` | The `productId` to be gifted. This should not be the ProductId of the gift product. |

#### Returns
`nil`


### PromptGamePassGift
Prompts the gamepass gifting GUI to the given `Player`.

#### Parameters
| Parameter | Type | Description | 
| ----------- | ----------- | ----------- |
| `player` | `Player` | The `Player` to prompt the gamepass gift gui to. |
| `gamePassId` | `number` | The `productId` to be gifted. This should not be the GamePassId of the gift gamepass. |

#### Returns
`nil`

### HasGiftId
Checks if the given `assetId` has an associated `GiftId`.

#### Parameters
| Parameter | Type | Description | 
| ----------- | ----------- | ----------- |
| `assetId` | `number` | The `assetId` to check for an associated `GiftId`. |
| `infoType` | `Enum.InfoType` | The type of item to check for an associated `GiftId`. |

#### Returns
`boolean`

### IsGiftId
Returns if the given `assetId` is a `GiftId`.

#### Parameters
| Parameter | Type | Description | 
| ----------- | ----------- | ----------- |
| `assetId` | `number` | The `assetId` to check to be a `GiftId`. |
| `infoType` | `Enum.InfoType` | The type of item to check. |

#### Returns
`boolean`

### GetProductGiftId
Returns the `GiftId` associated with `ProductId`. Returns `nil` if no `GiftId` is found.

#### Parameters
| Parameter | Type | Description | 
| ----------- | ----------- | ----------- |
| `productId` | `number` | The `ProductId` to check for an associated `GiftId`. |

#### Returns
`number?`

### GetGamePassGiftId
Returns the `GiftId` associated with `GamePassId`. Returns `nil` if no `GiftId` is found.

#### Parameters
| Parameter | Type | Description | 
| ----------- | ----------- | ----------- |
| `gamePassId` | `number` | The `GamePassId` to check for an associated `GiftId`. |

#### Returns
`number?`

### GetProductIdFromGiftId
Returns the `ProductId` associated with `giftId`. Returns `nil` if no `ProductId` is found.

#### Parameters
| Parameter | Type | Description | 
| ----------- | ----------- | ----------- |
| `giftId` | `number` | The `GiftId` to check for an associated `ProductId`. |

#### Returns
`number?`

### GetGamePassIdFromGiftId
Returns the `ProductId` associated with `giftId`. Returns `nil` if no `ProductId` is found.

#### Parameters
| Parameter | Type | Description | 
| ----------- | ----------- | ----------- |
| `giftId` | `number` | The `GiftId` to check for an associated `ProductId`. |

#### Returns
`number?`

### CreateReceipt
Creates a function to replace `MarketplaceService.ProcessReceipt`. When the `GiftId` of `productId` is purchased the function will be called. Must return `Enum.ProductPurchaseDecision.PurchaseGranted` for successful purchases.

#### Parameters
| Parameter | Type | Description | 
| ----------- | ----------- | ----------- |
| `productId` | `number` | The `ProductId` to listen for. This should not be `GiftId` |
| `f` | `function` | The function to be called when `GiftId` is purchased. `f` takes the `GiftReceiptInfo` as a parameter. |

#### Returns
`nil`

### UserOwnsGamePassAsync
Returns if `Player.UserId` either owns a gamepass or was gifted the gamepass. All `MarketplaceService:UserOwnsGamePassAsync` calls should be replaced with this method.

#### Parameters
| Parameter | Type | Description | 
| ----------- | ----------- | ----------- |
| `userId` | `number` | The `Player.UserId` to check `gamePassId` for. |
| `gamePassId` | `number` | The `GamePassId` to be checked. |

#### Returns
`boolean`


## Types
### [ProductInfo](https://create.roblox.com/docs/reference/engine/classes/MarketplaceService#GetProductInfo)
### GiftReceiptInfo
| Key | Type | Description | 
| ----------- | ----------- | ----------- |
| `PurchaseId` | `string` | A unique identifier for the specific purchase. |
| `PlayerId` | `number` | The user ID of the user who received the gift. |
| `PlayerPurchasedId` | `number` | The user ID of the user who purchased. |
| `PlaceIdWherePurchased` | `number` | The place ID in which the purchase was made. Depending on where the user is during gameplay, the purchase place's ID can be the same as or different from the current place's ID. |
| `CurrencySpent` | `number` | The amount of currency spent in the transaction. |
| `CurrencyType` | `Enum.CurrencyType` | The type of currency spent in the purchase; always [Enum.CurrencyType.Robux](https://create.roblox.com/docs/en-us/reference/engine/enums/CurrencyType#Robux) |
| `ProductPurchaseChannel` | `Enum.ProductPurchaseChannel` | How the user acquired the developer product. One of [Enum.ProductPurchaseChannel](https://create.roblox.com/docs/en-us/reference/engine/enums/ProductPurchaseChannel). |
