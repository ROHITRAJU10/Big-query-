# Big-query-
1. Tabulate the country code and the abbreviation of various countries according to International Debt report.

select
country_code, short_name
from `bigquery-public-data.world_bank_intl_debt.country_summary`
order by `country_code` asc

country_code short_name
AFG Afghanistan
AGO Angola
ALB Albania
ARG Argentina
ARM Armenia
AZE Azerbaijan
BDI Burundi
BEN Benin
BFA Burkina Faso
BGD Bangladesh
BGR Bulgaria
BIH Bosnia and Herzegovina
BLR Belarus
BLZ Belize
BOL Bolivia
BRA Brazil
BTN Bhutan
BWA Botswana
CAF Central African Republic
CHN China
CIV Côte d'Ivoire
CMR Cameroon
COD Dem. Rep. Congo
COG Congo
COL Colombia
COM Comoros
CPV Cabo Verde
CRI Costa Rica
DJI Djibouti
DMA Dominica
DOM Dominican Republic
DZA Algeria
EAP East Asia & Pacific (excluding high income)
ECA Europe & Central Asia (excluding high income)
ECU Ecuador
EGY Egypt
ERI Eritrea
ETH Ethiopia
FJI Fiji
GAB Gabon
GEO Georgia
GHA Ghana
GIN Guinea
GMB The Gambia
GNB Guinea-Bissau
GRD Grenada
GTM Guatemala
GUY Guyana
HND Honduras
HTI Haiti
IDN Indonesia
IDX IDA only
IND India
IRN Iran
JAM Jamaica
JOR Jordan
KAZ Kazakhstan
KEN Kenya
KGZ Kyrgyz Republic
KHM Cambodia
LAC Latin America & Caribbean (excluding high income)
LAO Lao PDR
LBN Lebanon
LBR Liberia
LCA St. Lucia
LDC Least developed countries: UN classification
LIC Low income
LKA Sri Lanka
LMC Lower middle income
LMY Low & middle income
LSO Lesotho
MAR Morocco
MDA Moldova
MDG Madagascar
MDV Maldives
MEX Mexico
MIC Middle income
MKD North Macedonia
MLI Mali
MMR Myanmar
MNA Middle East & North Africa (excluding high income)
MNE Montenegro
MNG Mongolia
MOZ Mozambique
MRT Mauritania
MUS Mauritius
MWI Malawi
NER Niger
NGA Nigeria
NIC Nicaragua
NPL Nepal
PAK Pakistan
PER Peru
PHL Philippines
PNG Papua New Guinea
PRY Paraguay
ROU Romania
RUS Russia
RWA Rwanda
SAS South Asia
SDN Sudan
SEN Senegal
SLB Solomon Islands
SLE Sierra Leone
SLV El Salvador
SOM Somalia
SRB Serbia
SSA Sub-Saharan Africa (excluding high income)
STP São Tomé and Principe
SWZ Eswatini
SYR Syrian Arab Republic
TCD Chad
TGO Togo
THA Thailand
TJK Tajikistan
TKM Turkmenistan
TLS Timor-Leste
TON Tonga
TUN Tunisia
TUR Turkey
TZA Tanzania
UGA Uganda
UKR Ukraine
UMC Upper middle income
UZB Uzbekistan
VCT St. Vincent and the Grenadines
VEN Venezuela
VNM Vietnam
VUT Vanuatu
WSM Samoa
XKX Kosovo
YEM Yemen
ZAF South Africa
ZMB Zambia
ZWE Zimbabwe


2. Mention the name and station id of bike stations which are situated in-between the latitude 40.74 N and 40.745 N.

select station_id,name,latitude
from `bigquery-public-data.new_york.citibike_stations`
where latitude between 40.74 and 40.745
order by latitude asc

station_id name latitude
537 Lexington Ave & E 24 St 40.74025878
402 Broadway & E 22 St 40.7403432
491 E 24 St & Park Ave S 40.74096374
3660 W 16 St & 8 Ave 40.741021509
3647 48 Ave & 30 Pl 40.7412830936
536 1 Ave & E 30 St 40.74144387
3120 Center Blvd & Borden Ave 40.74161
435 W 21 St & 6 Ave 40.74173969
3119 Vernon Blvd & 50 Ave 40.74232744
3608 Coming Soon: 5 St & 51 Ave 40.7423737
334 W 20 St & 7 Ave 40.74238787
3606 49 Ave & 21 St 40.74252
3210 Pershing Field 40.742677141
3472 W 15 St & 10 Ave 40.7427538287
3641 Broadway & W 25 St 40.7428687731
528 2 Ave & E 31 St 40.74290902
3659 W 17 St & 9 Ave 40.7429489166
3221 47 Ave & 31 St 40.743
540 Lexington Ave & E 29 St 40.7431155538
212 W 16 St & The High Line 40.74334935
470 W 20 St & 8 Ave 40.74345335
3658 W 18 St & 9 Ave 40.7435337325
476 E 31 St & 3 Ave 40.74394314
466 W 25 St & 6 Ave 40.74395411
527 E 33 St & 2 Ave 40.744023
501 FDR Drive & E 35 St 40.744219
3196 Riverview Park 40.7443187
3122 48 Ave & 5 St 40.7443632871
546 E 30 St & Park Ave S 40.74444921
3123 31 St & Thomson Ave 40.74469738
453 W 22 St & 8 Ave 40.74475148
446 W 24 St & 7 Ave 40.74487634
3611 Vernon Blvd & 47 Rd 40.7449067

3.Find the most populated area in the United States of America. and mention its geo id in order to enhance  the tracking speed.
SELECT census1.zipcode,census1.population,census1.geo_id
FROM `bigquery-public-data.census_bureau_usa.population_by_zip_2000` AS census1
JOIN `bigquery-public-data.census_bureau_usa.population_by_zip_2000` AS census2
ON (census1.zipcode = census2.zipcode)
order by `population` desc
LIMIT 1

zipcode population geo_id
00725 143987 8600000US00725

4.. What was the population growth rate in Afghanistan during the period 1979-1998?

select fertility1.country_name,fertility1.country_code,fertility2.growth_rate, year
from `bigquery-public-data.census_bureau_international.country_names_area`
as fertility1
join `bigquery-public-data.census_bureau_international.birth_death_growth_rates` as fertility2
on (
   fertility1.country_code = fertility2.country_code)
   limit 20

country_name country_code growth_rate year
Afghanistan AF -0.836 1979
Afghanistan AF -5.933 1980
Afghanistan AF -13.48 1981
Afghanistan AF -2.729 1982
Afghanistan AF 0.454 1983
Afghanistan AF 4.717 1984
Afghanistan AF 0.764 1985
Afghanistan AF -0.673 1986
Afghanistan AF -0.388 1987
Afghanistan AF 2.09 1988
Afghanistan AF 2.909 1989
Afghanistan AF -1.928 1990
Afghanistan AF 3.43 1991
Afghanistan AF 14.87 1992
Afghanistan AF 10.153 1993
Afghanistan AF 6.702 1994
Afghanistan AF 3.492 1995
Afghanistan AF 3.242 1996
Afghanistan AF 3.206 1997
Afghanistan AF 3.257 1998

5. Which two teams were part of the longest basket ball game of the year 2016? Mention the duration of the game as well.

select year, homeTeamName,awayTeamName,duration_minutes,
from `bigquery-public-data.baseball.schedules`
order by `duration_minutes` desc
limit 1



year homeTeamName awayTeamName duration_minutes
2016 Blue Jays Indians 373

6. Who are the top 10 most affordable providers of Cardio Thoracic treatment?

select provider_name, average_total_payments, drg_definition
from `bigquery-public-data.medicare.inpatient_charges_2011`
order by `average_total_payments` ASC
limit 10


provider_name average_total_payments drg_definition
UNIVERSITY HOSPITALS AHUJA MEDICAL CENTER 2673.0 313 - CHEST PAIN
THOMAS HOSPITAL 2682.642857 313 - CHEST PAIN
WEIRTON MEDICAL CENTER 2707.875 313 - CHEST PAIN
ST JOSEPHS HEALTHCARE SYSTEM 2708.0 313 - CHEST PAIN
KENTUCKIANA MEDICAL CENTER LLC 2718.277778 310 - CARDIAC ARRHYTHMIA & CONDUCTION DISORDERS W/O CC/MCC
OKLAHOMA HEART HOSPITAL SOUTH 2728.695906 313 - CHEST PAIN
TEXAS HEALTH HEART & VASCULAR HOSPITAL ARLINGTON 2731.0 313 - CHEST PAIN
BOONE HOSPITAL CENTER 2743.791045 313 - CHEST PAIN
THE HEART HOSPITAL AT DEACONESS GATEWAY LLC 2755.0 313 - CHEST PAIN
FORT LOUDOUN MEDICAL CENTER 2755.636364 313 - CHEST PAIN

7. List the top 3 ethereum blockchain addresses which account for the maximum tax count.

SELECT contracts.address, COUNT(1) AS tx_count
FROM `bigquery-public-data.ethereum_blockchain.contracts` AS contracts
JOIN `bigquery-public-data.ethereum_blockchain.transactions` AS transactions ON (transactions.to_address = contracts.address)
WHERE contracts.is_erc721 = TRUE
GROUP BY contracts.address
ORDER BY tx_count desc
LIMIT 3


address tx_count
0x06012c8cf97bead5deae237070f9587f8e7a266d 4391135
0xd73be539d6b2076bab83ca6ba62dfe189abc6bbe 427301
0x06a6a7af298129e3a2ab396c9c06f91d3c54aba8 396373

8. Provide infant mortality rate in Zimbabwe during late 1980s.

select country_name, year,infant_mortality
from `bigquery-public-data.census_bureau_international.mortality_life_expectancy`
order by `country_name` desc
limit 10

country_name year infant_mortality
Zimbabwe 1987 54.64
Zimbabwe 1985 56.71
Zimbabwe 1989 52.65
Zimbabwe 1988 53.64
Zimbabwe 1983 58.85
Zimbabwe 1991 57.28
Zimbabwe 1990 54.92
Zimbabwe 1986 55.67
Zimbabwe 1984 57.77
Zimbabwe 1982 59.99


9. List down the first 40 bicycle stations in London along with its name.

select name, id
from `bigquery-public-data.london_bicycles.cycle_stations`
order by `id` asc
limit 40

name id
"River Street , Clerkenwell" 1
"Phillimore Gardens, Kensington" 2
"Christopher Street, Liverpool Street" 3
"St. Chad's Street, King's Cross" 4
"Sedding Street, Sloane Square" 5
"Broadcasting House, Marylebone" 6
"Charlbert Street, St. John's Wood" 7
"Maida Vale, Maida Vale" 8
"New Globe Walk, Bankside" 9
"Park Street, Bankside" 10
"Brunswick Square, Bloomsbury" 11
"Malet Street, Bloomsbury" 12
"Scala Street, Fitzrovia" 13
"Belgrove Street , King's Cross" 14
"Great Russell Street, Bloomsbury" 15
"Cartwright Gardens , Bloomsbury" 16
"Hatton Wall, Holborn" 17
"Drury Lane, Covent Garden" 18
"Taviton Street, Bloomsbury" 19
"Drummond Street , Euston" 20
"Hampstead Road (Cartmel), Euston" 21
"Northington Street , Holborn" 22
"Red Lion Square, Holborn" 23
"British Museum, Bloomsbury" 24
"Doric Way , Somers Town" 25
"Ampton Street , Clerkenwell" 26
"Bouverie Street, Temple" 27
"Bolsover Street, Fitzrovia" 28
"Hereford Road, Bayswater" 29
"Windsor Terrace, Hoxton" 30
"Fanshaw Street, Hoxton" 31
"Leonard Circus , Shoreditch" 32
"Central House, Aldgate" 33
"Pancras Road, King's Cross" 34
"De Vere Gardens, Kensington" 36
"Penywern Road, Earl's Court" 37
"Abingdon Villas, Kensington" 38
"Shoreditch High Street, Shoreditch" 39
"Commercial Street, Shoreditch" 40
"Pindar Street, Liverpool Street" 41

10.Find the permit note number for tree 45986 found in San Fransisco City and also mention the date on which the tree was planted.

select tree_id,plant_date,permit_notes
from `bigquery-public-data.san_francisco_trees.street_trees`
locate where tree_id = 45986


tree_id plant_date permit_notes
45986 2001-12-06 00:00:00 UTC Permit Number 44451
