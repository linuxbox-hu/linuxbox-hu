---
excerpt: "1xx: Információ jellegű (Informational - Request received, continuing process)\r\n2xx:
  Sikeres (Success - The action was successfully received, understood, and accepted)\r\n3xx:
  Átirányítás (Redirection - Further action must be taken in order to complete the
  request)\r\n4xx: Kliens hiba (Client Error - The request contains bad syntax or
  cannot be fulfilled)\r"
categories:
- linux
layout: story
author: kecsi
mail: kecsi@linuxbox.hu
title: apache/httpd válasz kódok
created: 1107254116
---
1xx: Információ jellegű (Informational - Request received, continuing process)
2xx: Sikeres (Success - The action was successfully received, understood, and accepted)
3xx: Átirányítás (Redirection - Further action must be taken in order to complete the request)
4xx: Kliens hiba (Client Error - The request contains bad syntax or cannot be fulfilled)
5xx: Szerver hiba (Server Error - The server failed to fulfill an apparently valid request)

100: Tovább folytatom (Continue)
101 : Protokoll csere (Switching Protocols)
200 : OK
201 : Kész. (Created)
202 : Elfogadva (Accepted)
203 : Nem hiteles információ (Non-Authoritative Information)
204 : Üres tartalom (No Content)
205 : Rejtett tartalom (Reset Content)
206 : Részleges tartalom (Partial Content)
300 : Több választási lehetőség (Multiple Choices)
301 : Átmenetileg más helyre moztagott (Moved Permanently)
302 : Rendben (Found)
303 : Lásd másutt (See Other)
304 : Nem változott (Not Modified)
305 : Használj proxyt (Use Proxy)
307: Átmenetileg átirányitva (Temporary Redirect)
400 : Hibás kérés (Bad Request)
401 : Authentikáció szükséges (Unauthorized)
402 : Élőfizetőnek (Payment Required)
403 : Tiltott (Forbidden)
404 : Nincs találat (Not Found)
405 : Methódus nem megengedett (Method Not Allowed)
406 : Nem elfogadható (Not Acceptable)
407 : Proxy authentikáció szükséges (Proxy Authentication Required)
408 : Időtúllépés (Request Time-out)
409 : Konfliktus (Conflict)
410 : Eltűnt (Gone)
411 : Hossz szüskéges (Length Required)
412 : Előfeltétel nem teljesült (Precondition Failed)
413 : Kérés túl nagy (Request Entity Too Large)
414 : Kérés URL túl hosszú (Request-URI Too Large)
415 : Nem támogatott médiatípus (Unsupported Media Type)
416 : Kérés tartomány nem meghatározható (Requested range not satisfiable)
417 : (Expectation Failed)
500 : Belső szerver hiba (Internal Server Error)
501 : Nincs implemenálva (Not Implemented)
502 : Hibás kapu (Bad Gateway)
503 : Szolgáltatás nem elérhető (Service Unavailable)
504 : (Gateway Time-out)
505 : HTTP verzió nem támogatott (HTTP Version not supported)

<a href="http://www.w3.org/Protocols/rfc2616/rfc2616-sec6.html">forrás RFC</a>
