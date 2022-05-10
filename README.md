local settings = {repeatamount = 20}
                local mt = getrawmetatable(game)
                local old = mt.__namecall
                
                setreadonly(mt, false)
                
                task.spawn(function()
                mt.__namecall = function(self, ...)
                  local args = {...}
                  local method = getnamecallmethod();
                  if method == "FireServer" and self.Name == "Impact" then
                      for i = 1, settings.repeatamount do
                          old(self, ...)
                      end;
                  end;
                  return old(self, ...)
                end
                end)
                setreadonly(mt, true)
