## wireshark - Interactively dump and analyze network traffic
##### How to write dissector in lua?

In ~/.wireshark, create 1. init.lua 2. trivial.lua

1. init.lua
```lua
disable_lua = false
dofile("trivial.lua")
```

2. trivial.lua
```lua
-- init.lua
-- trivial protocol example
-- declare our protocol
trivial_proto = Proto("trivial","Trivial Protocol")
-- create a function to dissect it
function trivial_proto.dissector(buffer,pinfo,tree)
    pinfo.cols.protocol = "TRIVIAL"
    local subtree = tree:add(trivial_proto,buffer(),"Trivial Protocol Data")
    subtree:add(buffer(0,2),"The first two bytes: " .. buffer(0,2):uint())
    subtree = subtree:add(buffer(2,2),"The next two bytes")
    subtree:add(buffer(2,1),"The 3rd byte: " .. buffer(2,1):uint())
    subtree:add(buffer(3,1),"The 4th byte: " .. buffer(3,1):uint())
end
-- load the tcp.port table
tcp_table = DissectorTable.get("tcp.port")
-- register our protocol to handle tcp port 80
tcp_table:add(80,trivial_proto)
```

After all is done, relaunch wireshark, enjoy your work.

###### REFERENCE:

1. [Wireshark wiki](https://wiki.wireshark.org/Lua/Dissectors)
2. [GUIDE: Creating your own fast Wireshark plugin / dissector using LUA.](http://shloemi.blogspot.tw/2011/05/guide-creating-your-own-fast-wireshark.html)
