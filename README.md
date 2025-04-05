# GiftService
Adds support for users to gift gamepasses and products to other users. Automatically saves when a user purchases a gamepass or is gifted one to avoid repeat purchases.

## Important Information
All `MarketplaceService:UserOwnsGamePassAsync()` calls should be replaced with `GiftService:UserOwnsGamePassAsync()`. `GiftService:UserOwnsGamePassAsync()` will return true if the player either owns the gamepass or has been gifted the gamepass using GiftService.

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
| `assetId` | `number` | The `assetId` to check to beis a `GiftId`. |
| `infoType` | `Enum.InfoType` | The type of item to check. |

#### Returns
`boolean`

