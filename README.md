# pdns-queries-stats-cacti-template
====
URL : https://www.powerdns.com/recursor.html<br>

<br>
## Requirement<br>
OS:
 CentOS6<br>
Package:
 cacti-0.8.8b-7.el6.noarch<br>
 pdns-recursor-3.7.3-1.el6.x86_64<br>
<br>
<br>
## Install<br>
-- edit snmpd.conf<br>
$ cat snmpd.conf.add >> /etc/snmp/snmpd.conf<br>
<br>
-- check example<br>
$ cat /etc/snmp/snmpd.conf|grep dnsdist<br>
extend .1.3.6.1.4.1.18689.0.3 pdns-rec-queries /usr/local/bin/pdns-query-stats<br>
<br>
-- copy pdns-query-stats<br>
$ cp pdns-query-stats /usr/local/bin/<br>
$ chmod 755 /usr/local/bin/pdns-query-stats<br>
<br>
-- check example<br>
$ /usr/local/bin/pdns-query-stats<br>
A:2102 NS:60 TYPE3:1 TYPE4:1 CNAME:6 SOA:3091 TYPE7:1 TYPE8:1 TYPE9:1 TYPE10:1 TYPE11:1 PTR:329 HINFO:1 MINFO:1 MX:344 TXT:61 RP:1 AFSDB:1 TYPE19:1 TYPE20:1 TYPE21:1 TYPE22:1 TYPE23:1 TYPE24:1 KEY:1 TYPE26:1 TYPE27:1 AAAA:736 LOC:1 TYPE30:1 TYPE31:1 TYPE32:1 SRV:28 TYPE34:1 NAPTR:1 TYPE36:1 CERT:1 TYPE38:1 DNAME:1 TYPE40:1 OPT:1 TYPE42:1 DS:1 SSHFP:1 TYPE45:1 RRSIG:20318 NSEC:1 DNSKEY:1 TYPE49:1 NSEC3:1 NSEC3PARAM:1 TLSA:1 TYPE53:1 TYPE54:1 TYPE55:1 TYPE56:1 RKEY:1 TYPE58:1 TYPE59:1 TYPE60:1 TYPE61:1 TYPE62:1 TYPE63:1 TYPE64:1 SPF:1 TYPE100:1 TYPE101:1 TYPE102:1 TYPE103:1 TYPE104:1 ANY:30237<br>
<br>
-- copy pdns-queries-stats.sh<br>
$ cp pdns-queries-stats.sh /usr/share/cacti/scripts/<br>
$ chmod 755 /usr/share/cacti/scripts/pdns-queries-stats.sh<br>
<br>
-- check example<br>
$ /usr/share/cacti/scripts/pdns-queries-stats.sh 127.0.0.1 public<br>
A:2103 NS:60 TYPE3:1 TYPE4:1 CNAME:6 SOA:3093 TYPE7:1 TYPE8:1 TYPE9:1 TYPE10:1 TYPE11:1 PTR:329 HINFO:1 MINFO:1 MX:344 TXT:61 RP:1 AFSDB:1 TYPE19:1 TYPE20:1 TYPE21:1 TYPE22:1 TYPE23:1 TYPE24:1 KEY:1 TYPE26:1 TYPE27:1 AAAA:736 LOC:1 TYPE30:1 TYPE31:1 TYPE32:1 SRV:28 TYPE34:1 NAPTR:1 TYPE36:1 CERT:1 TYPE38:1 DNAME:1 TYPE40:1 OPT:1 TYPE42:1 DS:1 SSHFP:1 TYPE45:1 RRSIG:20320 NSEC:1 DNSKEY:1 TYPE49:1 NSEC3:1 NSEC3PARAM:1 TLSA:1 TYPE53:1 TYPE54:1 TYPE55:1 TYPE56:1 RKEY:1 TYPE58:1 TYPE59:1 TYPE60:1 TYPE61:1 TYPE62:1 TYPE63:1 TYPE64:1 SPF:1 TYPE100:1 TYPE101:1 TYPE102:1 TYPE103:1 TYPE104:1 ANY:30254<br>
<br>

## Notes
rec_control get-qtypelist の出力結果からクエリータイプ別の結果をグラフ化

