---
author: szimszon
categories:
- drupal
created: 1109168370
date: '2005-02-23T00:00:00Z'
excerpt: '<ol>\r\n<li>A modul letöltése: <a href="http://drupal.org/files/projects/i18n-4.5.0.tar.gz">http://drupal.org/files/projects/i18n-4.5.0.tar.gz</a></li>\r\n<li>Adatbázis bővítése:\r\nTábla létrehozása a modulnak, és módosítások:\r\n<code>\r\nCREATE TABLE i18n_node (\r\n  trid int4 NOT NULL default ''0'',\r\n  nid int4 NOT NULL default ''0'',\r\n  status int4 NOT NULL default ''0'', \r\n  PRIMARY KEY  (trid,nid)\r\n);\r\n\r\nALTER TABLE node ADD language char(2);\r\nALTER TABLE node ALTER language SET NOT NULL;\r\nALTER TABLE node ALTER language SET DEFAULT ''0'';\r\n\r\nALTER TABLE term_data ADD language char(2);\r\nALTER TABLE term_data ALTER language SET NOT NULL;\r'
title: I18n telepítése Postgresql adatbázissal Drupal 4.5.2-re
aliases:
- /node/33/
- /story/33/
---
<ol>
<li>A modul letöltése: <a href="http://drupal.org/files/projects/i18n-4.5.0.tar.gz">http://drupal.org/files/projects/i18n-4.5.0.tar.gz</a></li>
<li>Adatbázis bővítése:
Tábla létrehozása a modulnak, és módosítások:
<code>
CREATE TABLE i18n_node (
  trid int4 NOT NULL default '0',
  nid int4 NOT NULL default '0',
  status int4 NOT NULL default '0', 
  PRIMARY KEY  (trid,nid)
);

ALTER TABLE node ADD language char(2);
ALTER TABLE node ALTER language SET NOT NULL;
ALTER TABLE node ALTER language SET DEFAULT '0';

ALTER TABLE term_data ADD language char(2);
ALTER TABLE term_data ALTER language SET NOT NULL;
ALTER TABLE term_data ALTER language SET DEFAULT '0';

ALTER TABLE term_data ADD trid int4;
ALTER TABLE term_data ALTER trid set DEFAULT '0';
ALTER TABLE term_data ALTER trid set NOT NULL;
UPDATE term_data SET trid = '0';

ALTER TABLE locales_target DROP CONSTRAINT locales_target_lid_key;
ALTER TABLE locales_target ADD CONSTRAINT locales_target_lid_key UNIQUE (lid,locale);
</code>

A jelenlegi `node`-ok átállítása a megfelelő nyelvre (pl.: hu):
<code>
UPDATE node SET language = 'hu';
UPDATE term_data SET language = 'hu';
</code>
</li>
<li>Mindent lehet a leírásnak megfelelően végezni</li>
</ol>
<ol>
<li>Létre kell hozni egy <code>modules/i18n</code> könyvtárat és bele kell másolni a csomag teljes tartalmát.</li>
<li>Foltozni kell a `bootstrap.inc`, `module.inc`, `common.inc`, `node.module`, `taxonomy.module` (nekem gond nélkül ment 4.5.2-es Drupallal)</li>
<li><code>$i18n_languages = array("es" => "spanish", "en" => "english");</code>-et be kell írni a `includes/conf.php`-ba</li>
<li>továbbá a nyelvfüggő globális változókat (ld.: INSTALL.txt)</li>
</ol>
