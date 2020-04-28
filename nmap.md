# Remove Nmap Fingerprint

# nselib/http.lua:159
change nmap user-agent to other common user-agent


## tcpip.cc:729
nmap tcp scan defualt windows size is 1024, it can be easyly detacted by IDS/IPS device

change TCP windows size value 

```C
tcp->th_win = htons(1024); /* Who cares */. 
```
change `1024` to other value

## nselib/rdp.lua:211 
```lua
local cookie = "mstshash=nmap"
```
change `nmap` to other value

## osscan2.cc:2218
```C
static u8 patternbyte = 0x43; /* character 'C' */
```
change `0x43` to other hex string

## nmap-service-probes:13473
```
mstshash=nmap
```
change `nmap` to other value

## replace all "nmap" string in nmap-service-probes

```
OPTIONS sip:nm
```
replace SIP method to other, like `INVIKE`, and replace `nm` to other string
![SIP request messages](https://help.fortinet.com/fos50hlp/54/Content/FortiOS/fortigate-voip-guide-52/SIP-mes-media-pro-request.htm)

## nselib/http.lua:2601
```lua
-- The URLs used to check 404s
local URL_404_1 = '/nmaplowercheck' .. os.time(os.date('*t'))
local URL_404_2 = '/NmapUpperCheck' .. os.time(os.date('*t'))
local URL_404_3 = '/Nmap/folder/check' .. os.time(os.date('*t'))
```
change "nmap" to other string

## Global replace "Nmap NSE" string

