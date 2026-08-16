---
author: 1soproni
categories:
- debian
created: 1250516332
date: '2009-08-17T00:00:00Z'
title: watch mysql
---
ha valaki sql-ben tárolja a logjait, a hasonló módon helyettesítheti a megszokott tail -f paracsot:

watch -n 0,1 'mysql -u user -ppassword table -B -e "select from_unixtime(timestamp),username,cache_status,req_uri from (select * from access_log order by timestamp desc limit 0, 40) as s2 order by timestamp asc"'

ctrl+s pillanatnyi állapot megállítása 

Ha valaki még tud segíteni beszúrni egy WHERE cache_status = "TCP_DENIED" -et, annak megköszönöm.
Megoldás:
watch -n 0,1 'mysql -u user -ppassword table -B -e "select from_unixtime(timestamp),username,cache_status,req_uri from (select * from access_log_friss where cache_status = \"TCP_DENIED\" order by timestamp desc limit 0, 40) as s2 order by timestamp asc "'
