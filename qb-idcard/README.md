# qb-idcard

Simple id card you can use for **[qb-core](https://github.com/qbcore-framework/qb-core)**


## How to use
### Let's delete the default CreateUseableItem codes
+ qb-inventory > server > main.lua > Find and Delete 
 ```lua
QBCore.Functions.CreateUseableItem("driver_license", function(source, item)
	for k, v in pairs(QBCore.Functions.GetPlayers()) do
		local PlayerPed = GetPlayerPed(source)
		local TargetPed = GetPlayerPed(v)
		local dist = #(GetEntityCoords(PlayerPed) - GetEntityCoords(TargetPed))
		if dist < 3.0 then
			local gender = "Man"
			if item.info.gender == 1 then
				gender = "Woman"
			end
			TriggerClientEvent('chat:addMessage', v,  {
					template = '<div class="chat-message advert"><div class="chat-message-body"><strong>{0}:</strong><br><br> <strong>First Name:</strong> {1} <br><strong>Last Name:</strong> {2} <br><strong>Birth Date:</strong> {3} <br><strong>Gender:</strong> {4}<br><strong>Licenses:</strong> {5}</div></div>',
					args = {
						"Drivers License",
						item.info.firstname,
						item.info.lastname,
						item.info.birthdate,
						gender,
						item.info.type
					}
				}
			)
		end
	end
end)

QBCore.Functions.CreateUseableItem("id_card", function(source, item)
	for k, v in pairs(QBCore.Functions.GetPlayers()) do
		local PlayerPed = GetPlayerPed(source)
		local TargetPed = GetPlayerPed(v)
		local dist = #(GetEntityCoords(PlayerPed) - GetEntityCoords(TargetPed))
		if dist < 3.0 then
			local gender = "Man"
			if item.info.gender == 1 then
				gender = "Woman"
			end
			TriggerClientEvent('chat:addMessage', v,  {
					template = '<div class="chat-message advert"><div class="chat-message-body"><strong>{0}:</strong><br><br> <strong>Civ ID:</strong> {1} <br><strong>First Name:</strong> {2} <br><strong>Last Name:</strong> {3} <br><strong>Birthdate:</strong> {4} <br><strong>Gender:</strong> {5} <br><strong>Nationality:</strong> {6}<br><strong>Fingerprint:</strong> {7}</div></div>',
					args = {
						"ID Card",
						item.info.citizenid,
						item.info.firstname,
						item.info.lastname,
						item.info.birthdate,
						gender,
						item.info.nationality,
						item.info.fingerprint
					}
				}
			)
		end
	end
end)
```


+ server.cfg ```ensure qb-idcard or [qb] folder```
+ use item {show nui}
+ hide nui key {backspace}
