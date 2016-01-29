## tshark - Dump and analyze network traffic
##### Question : How to use packet counter?

```bash
$ tshark -r test.pcap -X lua_script:packet_counter.lua
```

packet_counter.lua

```lua
do
    packets = 0;
    local function init_listener()
        local tap = Listener.new("frame","ip.addr == 10.0.0.0/8")
        function tap.reset()
            packets = 0;
        end
        function tap.packet(pinfo,tvb,ip)
            packets = packets + 1
        end
        function tap.draw()
            print("Packets to/from 10.0.0./8",packets)
        end
    end
    init_listener()
end
```

###### OPTIONS:
__-r \<infile>__
> Read packet data from infile, can be any supported capture file format (including gzipped files).  It's not possible to use named pipes or stdin here!

__-X \<eXtension options>__
>Specify an option to be passed to a TShark module.  The eXtension option is in the form extension_key:value, where extension_key can be:```lua_script:lua_script_filename``` tells Wireshark to load the given script in addition to the default Lua scripts.

###### REFERENCE:

[1] [Wireshark Lua Examples](https://wiki.wireshark.org/Lua/Examples)
