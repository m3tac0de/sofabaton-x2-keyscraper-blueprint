# SofaBaton X2 Library Scraper for Home Assistant

[![Open your Home Assistant instance and show the blueprint import dialog with this blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fm3tac0de%2Fsofabaton-x2-keyscraper-blueprint%2Fblob%2Fmain%2Fblueprints%2Fscript%2Fsofabaton_scraper.yaml)

A utility script to extract `activity_id`, `device_id`, and `key_id` codes from the SofaBaton X2 Hub, so they can be used in Automations, Scripts and UIs.

## 🚀 Why this exists
With the [Sofabaton X2 integration](https://github.com/yomonpet/ha-sofabaton-hub), any command the X2 hub knows about can be triggered from Home Assistant.
Using the `remote` entity the integration adds for each configured hub, commands can be called like this:

```yaml
    action: remote.send_command
    target:
      entity_id: remote.HUB_NAME
    data:
      command:
        - type: KEY_TYPE
        - activity_id: ACTIVITY_ID
        - key_id: KEY_ID
```

Automations, scripts and UIs looking to implement this will need KEY_TYPE, ACTIVITY_ID and KEY_ID for each command they intend to trigger.

This blueprint fetches all of these for your Activities and/or Devices, and provides ready to use YAML showing how to use the codes retrieved.

## 🛠 Installation
1. Click the **Blue Import Button** above OR manually copy `sofabaton_scraper.yaml` to your `/config/blueprints/script/` folder.
   If installing manually, reload Scripts in **Developer tools > YAML**
3. Go to **Settings > Automations & Scenes > Scripts**.
4. Click **Create script** and select this blueprint from the list.

## 📖 How to use
1. **Select Remote:** Choose your SofaBaton X2 hub remote entity.
2. **Choose Mode:**
   - **Activities:** Retrieve codes for Keys, Macros and Favorites
   - **Devices:** Retrieve codes for your Devices
4. **Run Script:** Execute the script and wait (Device mode can take 10-30 seconds per device).
5. **Copy YAML:** Open your Notifications sidebar in Home Assistant to see the generated tables and code examples.

## ⚠️ Important Notes
- **Sofabaton X2 Integration:** You must have the official [Sofabaton X2 integration](https://github.com/yomonpet/ha-sofabaton-hub) installed and working.
- **Hub Performance:** The hub may become less responsive while the script is running.
- **Large Key Sets:** For AVRs or devices with 100+ keys, the hub may occasionally timeout. Usually the hub is able to return large keysets after a fresh restart.
