## wireshark - Interactively dump and analyze network traffic
##### Question : How to view packet tree of field?

```bash
$ wireshark -r test.pcap -X lua_script:packet_tree.lua
```

packet_tree.lua

```lua
-- This example iterates through the field tree of the packets, and prints out the tree field information in a text window.
-- It shows the current tree for the selected packet, but this does not mean it always shows the full tree,
-- because wireshark performs multiple dissection passes of a packet, with the initial pass only being high-level and not
-- dissecting fully (for performance reasons).  You can see this behavior better by changing line 30 of this example
-- to this, so it concatenates output instead of clearing it every time:
-- output = output .. "\nTree fields for packet #".. pinfo.number .. ":\n"

-- this only works in wireshark
if not gui_enabled() then return end

local output = ""    -- for the output we'll show in the text window
local tw = nil       -- the text window
-- function to refresh the text window
local function updateWindow()
    if tw then tw:set(output) end
end

-- calling tostring() on random FieldInfo's can cause an error, so this func handles it
local function getstring(finfo)
    local ok, val = pcall(tostring, finfo)
    if not ok then val = "(unknown)" end
    return val
end

-- create a new protocol so we can register a post-dissector
local myproto = Proto("tree_view","Dummy proto to view tree")

-- the dissector function callback
function myproto.dissector(tvb,pinfo,tree)
    output = output.. "\nTree fields for packet #".. pinfo.number .. ":\n"
    -- get a table of all FieldInfo objects
    local fields = { all_field_infos() }
    for ix, finfo in ipairs(fields) do
        output = output .. "\t[" .. ix .. "] " .. finfo.name .. " = " .. getstring(finfo) .. "\n"
    end
    updateWindow()
end
-- register our new dummy protocol for post-dissection
register_postdissector(myproto)


-- now we create the menu function for this, which creates a text window to display this stuff
local function menu_view_tree()
    tw = TextWindow.new("Tree View")
    tw:set_atclose(function() tw = nil end)
    updateWindow()
end

-- add this to the Tools->Lua submenu
register_menu("Lua/Tree View", menu_view_tree, MENU_TOOLS_UNSORTED)
```

###### OPTIONS:
__-r \<infile>__
> Read packet data from infile, can be any supported capture file format (including gzipped files).  It's not possible to use named pipes or stdin here!

__-X \<eXtension options>__
>Specify an option to be passed to a TShark module.  The eXtension option is in the form extension_key:value, where extension_key can be:```lua_script:lua_script_filename``` tells Wireshark to load the given script in addition to the default Lua scripts.

###### REFERENCE:

[1] [Wireshark Lua Examples](https://wiki.wireshark.org/Lua/Examples)
