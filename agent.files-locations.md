---
name: Agent Files Locations
description: Path to add to chat.agentFilesLocations for agent or prompt to be used by VSCode tools
---

# Add agent-name files location 
# Each path, subpath must be inclued as experimental recursive UI option don't work
ex: ".github/agents/time-management": true,
ex: ".github/agents/time-management/timestamps": true,

in json block
"chat.agentFilesLocations": {
},

in file `C:\Users\rodge\AppData\Roaming\Code\User\settings.json`
or via settings.json.lnk
at end of file
