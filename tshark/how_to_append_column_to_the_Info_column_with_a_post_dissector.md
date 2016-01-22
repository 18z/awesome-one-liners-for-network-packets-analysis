## tshark - Dump and analyze network traffic
##### Question : How to append column to the Info column with a post-dissector?

```bash
$ tshark -r test.pcap -X lua_script:append_column.lua
```

append_column.lua

```lua
-- Append "<dst> -> <src>" to the Info column with a post-dissector.
-- (Taps are not guaranteed to be run at a point when they can set the
-- column text, so they can't be used for this.)

-- create a new protocol so we can register a post-dissector
local myproto = Proto("swapper","Dummy proto to edit info column")

-- the dissector function callback
function myproto.dissector(tvb,pinfo,tree)
    pinfo.cols.info:append(" " .. tostring(pinfo.dst).." -> "..tostring(pinfo.src))
end
-- register our new dummy protocol for post-dissection
register_postdissector(myproto)
```

###### OPTIONS:
__-r \<infile>__
> Read packet data from infile, can be any supported capture file format (including gzipped files).  It's not possible to use named pipes or stdin here!

__-X \<eXtension options>__
>Specify an option to be passed to a TShark module.  The eXtension option is in the form extension_key:value, where extension_key can be:```lua_script:lua_script_filename``` tells Wireshark to load the given script in addition to the default Lua scripts.

###### REFERENCE:

[1] [Wireshark Lua Examples](https://wiki.wireshark.org/Lua/Examples)
