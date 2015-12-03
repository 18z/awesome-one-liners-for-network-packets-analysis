## tshark - Dump and analyze network traffic
##### Question : How to customize ouput format?
```bash
$ tshark -i "eth0" -T fields \
    -E separator=, -E aggregator=| -E quote=d \
    -e frame.number -e ip.addr -e udp -e _ws.col.Info
```

###### OPTIONS:


__-T fields|pdml|ps|psml|text__

>Set the format of the output when viewing decoded packet data. The options are one of:

>**fields** The values of fields specified with the **-e** option, in a form specified by the **-E** option. For example,

>>-T fields -E separator=, -E quote=d

>would generate comma-separated values (CSV) output suitable for importing into your favorite spreadsheet program.

>**pdml** Packet Details Markup Language, an XML-based format for the details of a decoded packet. This information is equivalent to the packet details printed with the **-V** flag.

>**ps** PostScript for a human-readable one-line summary of each of the packets, or a multi-line view of the details of each of the packets, depending on whether the **-V** flag was specified.

>**psml** Packet Summary Markup Language, an XML-based format for the summary information of a decoded packet. This information is equivalent to the information shown in the one-line summary printed by default.

>**text** Text of a human-readable one-line summary of each of the packets, or a multi-line view of the details of each of the packets, depending on whether the **-V** flag was specified. This is the default.


__-E \<field print option>__

>Set an option controlling the printing of fields when **-T fields** is selected.

>Options are:

>**header=y|n** If y, print a list of the field names given using -e as the first line of the output; the field name will be separated using the same character as the field values. Defaults to **n**.

>**separator=/t|/s|<character>** Set the separator character to use for fields. If **/t** tab will be used (this is the default), if **/s**, a single space will be used. Otherwise any character that can be accepted by the command line as part of the option may be used.

>**occurrence=f|l|a** Select which occurrence to use for fields that have multiple occurrences. If **f** the first occurrence will be used, if **l** the last occurrence will be used and if **a** all occurrences will be used (this is the default).

>**aggregator=,|/s|<character>** Set the aggregator character to use for fields that have multiple occurrences. If **,** a comma will be used (this is the default), if **/s**, a single space will be used. Otherwise any character that can be accepted by the command line as part of the option may be used.

>**quote=d|s|n** Set the quote character to use to surround fields. **d** uses double-quotes, **s** single-quotes, **n** no quotes (the default).


__-e \<field>__

>Add a field to the list of fields to display if **-T fields** is selected. This option can be used multiple times on the command line. At least one field must be provided if the **-T fields** option is selected. Column names may be used prefixed with "_ws.col."

>Example: **-e frame.number -e ip.addr -e udp -e _ws.col.Info**

>Giving a protocol rather than a single field will print multiple items of data about the protocol as a single field. Fields are separated by tab characters by default. **-E** controls the format of the printed fields.
