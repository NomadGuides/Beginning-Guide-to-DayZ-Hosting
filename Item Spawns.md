Here's a Markdown version of the guide for editing item spawns in DayZ SA:

```markdown
# Editing Item Spawns in DayZ SA

To edit the amount of a select item that spawns on the map, you need to modify the `types.xml` file. Here's a basic overview of the key attributes in the `types.xml` file and their effects:

## Key Attributes in `types.xml`

- **Nominal**: 
  - Defines how many instances of this item can be on the map at once.

- **Lifetime**: 
  - Specifies the lifetime of an item once it is spawned, in seconds.

- **Restock**: 
  - Indicates the amount of time that needs to pass before the item can spawn again.

- **Min**: 
  - Sets the minimum amount of this item that will spawn on the map.

- **QuantMin**: 
  - Determines the minimum quantity of consumables within the item. 
  - Value ranges from `-1.0%` (empty) to `100.0%` (full). 
  - For example, how many bullets are in an ammo box or how much water is in a bottle.

- **QuantMax**: 
  - Determines the maximum quantity of consumables within the item. 
  - Value ranges from `-1.0%` (empty) to `100.0%` (full).

- **Cost**: 
  - Determines the spawn chance of the item. 

- **Category**: 
  - Specifies the category of the item, which affects how and where the item spawns. Examples include Weapons, Tools, Containers, Clothes, etc.

- **Usage**: 
  - Indicates the area or group where the item will spawn. Examples include Farm, Industrial, Medic, Hunting, etc.

- **Value**: 
  - Specifies the value group of the item, which affects how and where the item spawns. Examples include Tier1, Tier2, Tier3, etc.

## Useful Tool

For setting up your `types.xml` file, you can use the [Types to Expansion Market Converter UI](https://github.com/Ninjin89/Types-to-Expansion-Market-Converter-UI/releases/tag/v2.0.5.8). This tool helps simplify the configuration of item spawns.

## Example

Here is a simplified example of how a typical item entry in `types.xml` might look:

```xml
<Type name="ItemName">
    <Nominal>10</Nominal>
    <Lifetime>3600</Lifetime>
    <Restock>1800</Restock>
    <Min>1</Min>
    <QuantMin>10.0</QuantMin>
    <QuantMax>100.0</QuantMax>
    <Cost>1</Cost>
    <Category>Tools</Category>
    <Usage>Farm</Usage>
    <Value>Tier2</Value>
</Type>
```

Feel free to adjust these values according to your preferences and server needs.
```

This Markdown guide provides a concise explanation of the `types.xml` attributes and includes a link to a useful tool for configuring item spawns. Adjust the details as needed for your documentation!
