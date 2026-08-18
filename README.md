# CHMA Factions

Custom **Arma Reforger faction addon** for **Chimera PMC (CHMA)**.

This addon defines the playable Chimera PMC faction and its associated character prefabs, loadouts and Campaign/Conflict configuration.

The project is used to bring CHMA's equipment and role-specific characters together into a faction that can be selected and used within Arma Reforger scenarios.

## Dependencies

The following Arma Reforger addons are required:

* **RHS - Content Pack 01**
* **RHS - Status Quo**
* **RHS - Content Pack 02**
* **GMFX - Game Master Effects**
* **Explosive mod**
* **M18 Claymore - ACE Explosives Compatibility Patch**
* **Flair's Tactical Gear**
* **Powerful Flashlights**
* **Wp Weapon pack**
* **Dubious Tactical Overhaul - Extended 3.3**
* **Zeliks Character**
* **CHMA Vehicles**
* **CHMA Gear Pack**
* **CHMA PMC Patches**
* **WP - Vanilla Replacement**
* **ACE Reloaded**
* **ACE_EX**
* **Tactical Flava**
* **Sierra Golf Weapons**
* **Blackheart Equipment**
* **[Blacklist]ZeliksRevolution**
* **No Ghillie for nVision**

These dependencies must be installed and enabled in Arma Reforger Workbench when developing, modifying or testing the addon.

Because the faction prefabs reference equipment and resources from several external projects, removing a dependency without first removing or replacing the affected references may cause broken prefabs, missing resources or failure to load the faction correctly.

## Project Structure

The project currently contains the main faction configuration and CHMA-specific character prefabs.

```text
Configs/
└── Factions/
    └── US_Campaign.conf

Prefabs/
└── Characters/
    ├── Campaign/
    │   └── Final/
    │       └── BLUFOR/
    │           └── US_army/
    └── Factions/
        └── BLUFOR/
            └── US_Army/
```

### Faction Configuration

```text
Configs/Factions/US_Campaign.conf
```

This configuration defines the **Chimera PMC** Campaign faction and connects the faction to its CHMA-specific character and role prefabs.

It also controls faction-level resources such as:

* Faction name
* Faction icon
* Faction flag
* Faction flag material
* Available player role/loadout prefabs
* Campaign role presets

### Character Prefabs

CHMA-specific player characters are maintained beneath:

```text
Prefabs/Characters/
```

These prefabs provide the equipment and loadouts used by Chimera PMC players.

The repository contains both Campaign character prefabs and faction-specific BLUFOR character prefabs.

## Development

This addon is developed using the **Arma Reforger Workbench**.

Clone the repository into your local Reforger addons directory:

```text
Documents\My Games\ArmaReforger\addons\CHMA-PMC-CHMA-Factions
```

Open:

```text
addon.gproj
```

through Arma Reforger Workbench.

Before modifying the project:

1. Ensure all required dependencies are installed.
2. Enable the dependencies in Workbench.
3. Allow Workbench to finish processing resources.
4. Check the console for missing-resource or dependency errors.

The project ID is:

```text
CHMAFactions
```

## Modifying

This repository should remain focused on the **CHMA faction and its associated character/loadout configuration**.

Faction-specific equipment should generally be sourced from the appropriate CHMA equipment addon rather than duplicated into this project.

For example:

* Vehicles belong in **CHMA Vehicles**
* Equipment and uniforms belong in **CHMA Gear Pack**
* Unit patches belong in **CHMA PMC Patches**
* Faction definitions and faction-specific character loadouts belong here

When modifying faction characters:

1. Locate the appropriate character prefab.
2. Make changes using inheritance where practical.
3. Avoid directly modifying third-party source prefabs.
4. Verify every referenced weapon, uniform and item belongs to an enabled dependency.
5. Check the resulting character in-game.
6. Verify that the corresponding faction role still points to the correct prefab.

## Adding or Changing Roles

When creating a new role or changing an existing role, both the character prefab and faction configuration may need to be updated.

The faction configuration currently references role-specific player prefabs for roles such as:

* Rifleman
* Grenadier
* Machine Gunner
* Officer
* Sniper
* Medical roles
* Squad leadership roles

When adding a new role:

1. Create or inherit the required character prefab.
2. Configure the intended equipment and inventory.
3. Save the prefab within the existing CHMA character structure.
4. Add the prefab resource to the appropriate faction role preset.
5. Test the role through the actual faction selection system.

Do not simply create a character prefab and assume it will become available to the faction; it must also be referenced by the appropriate faction configuration where required.

## Loadouts

Character equipment should be configured through the appropriate character/loadout prefab rather than hard-coded into unrelated faction resources.

When changing a loadout:

* Check weapon and magazine compatibility.
* Check attachment compatibility.
* Check inventory capacity.
* Check medical supplies.
* Check grenades and explosives.
* Check radios or specialist equipment where applicable.
* Check uniform, vest, backpack and headgear references.
* Confirm that all referenced resources exist in the current dependency set.

Avoid creating unnecessary duplicate prefabs where an inherited CHMA base prefab can be used.

## Faction Configuration

Changes to:

```text
Configs/Factions/US_Campaign.conf
```

should be made carefully.

This file controls important faction-level configuration including the playable **Chimera PMC** identity and available role resources.

After changing the faction configuration, verify:

* Chimera PMC appears correctly as a faction.
* The CHMA faction name displays correctly.
* The CHMA icon displays correctly.
* The CHMA flag displays correctly.
* All configured roles can be selected.
* All configured character prefabs spawn correctly.
* No referenced prefab produces missing-resource errors.
* Campaign/Conflict functionality continues to work.

## Testing

Before committing changes:

* Open the project without missing-resource errors.
* Check the Workbench console.
* Confirm all dependencies load correctly.
* Spawn every character prefab that was changed.
* Check uniforms and equipment.
* Check weapons and attachments.
* Check inventory contents.
* Check role-specific equipment.
* Check faction icon and flag assets.
* Verify the faction appears correctly in the intended scenario.
* Verify changed roles can be selected.
* Test player spawning.
* Test respawning where applicable.
* Test the faction in multiplayer.

Changes to faction configuration or character prefabs should be tested using the normal **CHMA Reforger modset** before release.

Where the faction is intended for Conflict, it should also be tested on a Conflict scenario rather than relying only on direct prefab spawning in Workbench.

## Dependency Changes

Do not add a dependency simply because it is available in the normal CHMA modset.

A dependency should only exist where this project directly references resources provided by that addon.

When introducing a new dependency:

1. Add it to the Workbench project.
2. Confirm that it is genuinely required by this addon.
3. Add it to the dependency list in this README.
4. Test the project without unrelated development addons enabled.

When removing a dependency, search the project for references to that addon first.

## Git

Only files required to develop, build and maintain the addon should be committed.

Before committing:

* Review all changed files.
* Check for accidentally deleted resources.
* Check for broken resource references.
* Include required `.meta` files.
* Check that dependencies have not been unintentionally changed.
* Test affected character prefabs.
* Test affected faction configuration.
* Use a commit message that clearly describes the change.

Example commit messages:

```text
Update CHMA Rifleman loadout
```

```text
Add CHMA Squad Leader faction prefab
```

```text
Update Chimera PMC Campaign roles
```

```text
Fix CHMA faction character equipment
```

## Notes

This addon acts as the faction layer between CHMA's other equipment addons and Arma Reforger's faction, character and Campaign/Conflict systems.

Changes made to **CHMA Gear Pack**, **CHMA Vehicles**, **CHMA PMC Patches** or other dependency projects may therefore require corresponding changes to character prefabs in this repository.

Keep faction configuration and role-specific character setup here; keep the actual reusable equipment assets within their respective CHMA repositories.

If a future change introduces a new dependency, unusual Workbench requirement, special faction configuration or non-obvious relationship between prefabs, document it in this README.
