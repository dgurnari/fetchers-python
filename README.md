# fetchers-python
COVID19 data source fetchers written in Python3

Currently implemented fetchers:

| Name     | Country | [Code](https://www.nationsonline.org/oneworld/country_code_list.htm) | Source | Status | Regional levels mapping |
|----------|---------|------|--------|--------|-------------------------|
| POL_WIKI | Poland | POL  | [Wikipedia](https://en.wikipedia.org/wiki/2020_coronavirus_pandemic_in_Poland) | candidate | adm_area_1: NA or Voivodeship, adm_area_2: NA |

Explanation of status:
- Draft: being developed, should not be tested yet
- Candidate: development complete, being tested on a private test database
- Release: tested, data are fed into the official public database


## Database structure

Infections table: see https://covid19db.github.io/data.html
- source: code describing the source of information. See table above.
- date: day of the statistics.
- country: English name for the country.
- countrycode: ISO ALpha-3 code of the country.
- adm_area_1: First-level administrative country subdivision; for example a "state" within United States, a
	"province" within China or Canada.
- adm_area_2: Second-level administrative country subdivision; for example an Italian "region", a UK "county".
- adm_area_3: Third-level administrative country subdivision; for example a city, a urban area or an Italian "province".
- tested: number of people tested.
- confirmed (cumulative): number of confirmed infections.
- recovered (cumulative): number of people who has been confirmed and has
	healed.
- hospitalised (cumulative): number of people who has been confirmed and has
	been hospitalised.
- hospitalised_icu (cumulative): number of people who has been confirmed and has
	been hospitalised and had to be put in intensive care.
- quarantined (cumulative): number of people who has been confirmed and has
	been quarantined in their home.


## Develop and test

You need:
- Python3
- Running instance of a PostgreSQL database
- (optional) Docker


## Run locally

1. Add the `DB_ADDRESS`, `DB_PORT`, `DB_NAME`, `DB_USERNAME` and `DB_PASSWORD` environment variables
2. Install requirements ```pip install -r requirements.txt```
3. Run fetcher `python3 ./main.py`

## Run locally using Docker

1. Add the `DB_ADDRESS`, `DB_PORT`, `DB_NAME`, `DB_USERNAME` and `DB_PASSWORD` environment variables
2. Run ```docker-compose up```

## Contribute

**We need fetchers!**

Create a fetcher for a country that is not listed yet and send us a pull request.
Use only official sources, or sources derived from official sources.

You can find example code for fetcher in /src/plugins/EXAMPLE/example_fetcher.py
