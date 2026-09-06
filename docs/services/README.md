# OSINT service capability index

One page per CreepyEYE PRO scan module. Each page lists the **full upstream provider capability**, what **CreepyEYE actually uses** today, the fields shown on the entity card, and the API-key variable name for [BYOK](../../README.md#bring-your-own-key-byok).

> Modules whose provider key you have not set are skipped during a scan — that is normal.

| service_id | Provider | Category | Query types | Doc |
|------------|----------|----------|-------------|-----|
| `abuseipdb_lookup` | AbuseIPDB | network | ip, network | [abuseipdb_lookup.md](abuseipdb_lookup.md) |
| `alienvault_otx_intel` | AlienVault OTX | intelligence | ip, network | [alienvault_otx_intel.md](alienvault_otx_intel.md) |
| `builtwith_intel` | BuiltWith | intelligence | domain, network | [builtwith_intel.md](builtwith_intel.md) |
| `ccrawl_intel` | Common Crawl | intelligence | domain | [ccrawl_intel.md](ccrawl_intel.md) |
| `censys_lookup` | Censys | network | ip, network | [censys_lookup.md](censys_lookup.md) |
| `clearbit_domain_lookup` | Clearbit | people | domain | [clearbit_domain_lookup.md](clearbit_domain_lookup.md) |
| `clearbit_lookup` | Clearbit | people | email | [clearbit_lookup.md](clearbit_lookup.md) |
| `darkowl` | DarkOwl Vision | breaches | email, username | [darkowl.md](darkowl.md) |
| `dehashed` | DeHashed | breaches | email, username | [dehashed.md](dehashed.md) |
| `emailrep_io_lookup` | EmailRep.io | people | email | [emailrep_io_lookup.md](emailrep_io_lookup.md) |
| `exiftool` | ExifTool | integrations | photo | [exiftool.md](exiftool.md) |
| `fullcontact_lookup` | FullContact | people | name | [fullcontact_lookup.md](fullcontact_lookup.md) |
| `geoip_lookup` | GeoIP API (geoipapi.com) | network | ip, network | [geoip_lookup.md](geoip_lookup.md) |
| `geonames_lookup` | GeoNames | network | ip, network | [geonames_lookup.md](geonames_lookup.md) |
| `greynoise_lookup` | GreyNoise | network | ip, network | [greynoise_lookup.md](greynoise_lookup.md) |
| `haveibeenpwned` | Have I Been Pwned | breaches | email, username | [haveibeenpwned.md](haveibeenpwned.md) |
| `hunter_io_lookup` | Hunter.io | people | email | [hunter_io_lookup.md](hunter_io_lookup.md) |
| `intelligencex_intel` | Intelligence X | breaches | email, username | [intelligencex_intel.md](intelligencex_intel.md) |
| `ip_api_lookup` | IP-API | network | ip, network | [ip_api_lookup.md](ip_api_lookup.md) |
| `ipinfo_lookup` | Ipinfo | network | ip, network | [ipinfo_lookup.md](ipinfo_lookup.md) |
| `ipqualityscore_lookup` | IPQualityScore | network | ip, network | [ipqualityscore_lookup.md](ipqualityscore_lookup.md) |
| `ipstack_lookup` | IPStack (Apilayer) | network | ip, network | [ipstack_lookup.md](ipstack_lookup.md) |
| `numverify_lookup` | NumVerify (Apilayer) | network | phone | [numverify_lookup.md](numverify_lookup.md) |
| `pastebin_scraper` | Pastebin (scrape) | breaches | email, username | [pastebin_scraper.md](pastebin_scraper.md) |
| `pdl_lookup` | People Data Labs | people | name | [pdl_lookup.md](pdl_lookup.md) |
| `phoneinfo_lookup` | PhoneInfoAPI | network | phone | [phoneinfo_lookup.md](phoneinfo_lookup.md) |
| `pipl_lookup` | Pipl | people | name | [pipl_lookup.md](pipl_lookup.md) |
| `recon_ng_lookup` | Recon-ng | integrations | domain | [recon_ng_lookup.md](recon_ng_lookup.md) |
| `search_by_sites_username` | CreepyEYE (multi-site HTTP probes) | username | username | [search_by_sites_username.md](search_by_sites_username.md) |
| `securitytrails_lookup` | SecurityTrails | network | ip, network | [securitytrails_lookup.md](securitytrails_lookup.md) |
| `sherlock` | Sherlock (via Apify actor or local CLI) | username | username | [sherlock.md](sherlock.md) |
| `shodan_scan` | Shodan | network | ip, network | [shodan_scan.md](shodan_scan.md) |
| `snusbase` | Snusbase | breaches | email, username | [snusbase.md](snusbase.md) |
| `spiderfoot` | SpiderFoot | integrations | domain, email | [spiderfoot.md](spiderfoot.md) |
| `telegram_osint_lookup` | Telegram (Telethon MTProto) | people | username | [telegram_osint_lookup.md](telegram_osint_lookup.md) |
| `virustotal_intel` | VirusTotal | intelligence | domain, ip, network | [virustotal_intel.md](virustotal_intel.md) |
| `whitepages_lookup` | Whitepages Pro | people | name, phone | [whitepages_lookup.md](whitepages_lookup.md) |
| `whoisxml_lookup` | WhoisXML API | network | domain, ip, network | [whoisxml_lookup.md](whoisxml_lookup.md) |
