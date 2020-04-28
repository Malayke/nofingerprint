# nofingerprint
remove common pentest tools fingerprint

Inspired by [al0ne/Nmap_Bypass_IDS](https://github.com/al0ne/Nmap_Bypass_IDS), I listed some nmap scaner detactable fingerprint

## Remove Nmap Fingerprint

### [nselib/http.lua](https://github.com/nmap/nmap/blob/master/nselib/http.lua#L159)
```c
USER_AGENT = stdnse.get_script_args('http.useragent') or "Mozilla/5.0 (compatible; Nmap Scripting Engine; https://nmap.org/book/nse.html)"
```
change nmap user-agent to other common user-agent


### [tcpip.cc](https://github.com/nmap/nmap/blob/master/tcpip.cc#L733)
```c
  if (window)
    tcp->th_win = htons(window);
  else
    tcp->th_win = htons(1024); /* Who cares */
```
nmap tcp scan defualt windows size is `1024`, it can be easyly detacted by IDS/IPS device

so it should be change to other value 

### [nselib/rdp.lua](https://github.com/nmap/nmap/blob/master/nselib/rdp.lua#L211)
```lua
local cookie = "mstshash=nmap"
```
change `nmap` to other value

### osscan2.cc:2218
```C
static u8 patternbyte = 0x43; /* character 'C' */
```
change `0x43` to other hex string

### nmap-service-probes:13473
```
mstshash=nmap
```
change `nmap` to other value

### Replace all "nmap" string in `nmap-service-probes` file

```
OPTIONS sip:nm
```
replace SIP method to other, like `INVIKE`, and replace `nm` to other string
[SIP request messages](https://help.fortinet.com/fos50hlp/54/Content/FortiOS/fortigate-voip-guide-52/SIP-mes-media-pro-request.htm)

### nselib/http.lua:2601
```lua
-- The URLs used to check 404s
local URL_404_1 = '/nmaplowercheck' .. os.time(os.date('*t'))
local URL_404_2 = '/NmapUpperCheck' .. os.time(os.date('*t'))
local URL_404_3 = '/Nmap/folder/check' .. os.time(os.date('*t'))
```
change `nmap` to other string

### Global replace "Nmap NSE" string

### change default behavior when using nmap
1. If no host discovery options are given, Nmap sends an ICMP echo request, a TCP SYN packet to port 443, a TCP ACK packet to port 80, and an ICMP timestamp request.

so can set `-PS22,135,445` flag to this behavior


