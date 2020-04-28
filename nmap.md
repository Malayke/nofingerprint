# Remove Nmap Fingerprint

## File: tcpip.cc:729
```C
tcp->th_win = htons(1024); /* Who cares */. 
```

change `1024` to other value

## File: nselib/rdp.lua:211 
```lua
local cookie = "mstshash=nmap"
```
change `nmap` to other value

## File: osscan2.cc:2218
```C
static u8 patternbyte = 0x43; /* character 'C' */
```
change `0x43` to other hex string

## File: nmap-service-probes:13473
```
mstshash=nmap
```
change `nmap` to other value

## replace all "nmap" string in nmap-service-probes

```
OPTIONS sip:nm
```
replace SIP method to other, like `INVIKE`, and replace `nm` to other string


## File: nselib/http.lua:2601
```lua
-- The URLs used to check 404s
local URL_404_1 = '/nmaplowercheck' .. os.time(os.date('*t'))
local URL_404_2 = '/NmapUpperCheck' .. os.time(os.date('*t'))
local URL_404_3 = '/Nmap/folder/check' .. os.time(os.date('*t'))
```
change "nmap" to other string
