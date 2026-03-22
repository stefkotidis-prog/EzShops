# 📦 Shop Items & Pricing (shop.yml)

The `shop.yml` file is where you define every item available in your server's shop, along with its base price and special properties.

---

## 💰 Basic Item Configuration

Each item is identified by its Minecraft Material Name. Here is how a basic setup looks:

```yaml
items:
  DIAMOND:
    buy: 100.0          # Price to buy from shop
    sell: 50.0          # Price received when selling
    
  SPAWNER:
    buy: 10000.0
    sell: -1            # -1 means the item cannot be sold
```

---

## ⚙️ Available Settings Overview

Below is the complete list of configuration options available for each item. These allow you to customize everything from GUI positioning to dynamic pricing behavior.

| Property | Type | Description |
|----------|------|-------------|
| `buy` | number | Price to purchase from shop (-1 = not buyable) |
| `sell` | number | Price received when selling to shop (-1 = not sellable) |
| `slot` | number | Specific slot position in the category GUI |
| `material` | string | Valid Minecraft material name |
| `display-name` | string | Custom name shown in the GUI (supports color codes) |
| `lore` | list | Multi-line description shown in the item tooltip |
| `amount` | number | Number of items per single purchase (default: 1) |
| `permission` | string | Custom permission node required to interact with this item |
| `stock-market` | boolean | If true, the price will fluctuate based on global stock settings |
| `dynamic.enabled` | boolean | Enables/disables individual dynamic pricing for this item |
| `item-type` | string | Delivery method: `ITEM` (default), `COMMAND` (runs a command instead), or `NONE`. |

---

## 🚀 Specialized Item Types

### Command-Based Items
You can sell "actions" instead of physical items by setting the `item-type` to `COMMAND`.

```yaml
items:
  GOLD_INGOT:
    display-name: "&6VIP Rank"
    item-type: "COMMAND"
    buy: 5000.0
    on-buy:
      - "lp user {player} parent add vip"
```