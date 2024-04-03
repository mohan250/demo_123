name: MyProject
sla_profiles:
- name: MySlaProfile
  thresholds:
  - avg-request-resp-time warn >= 200ms fail >= 500ms per test
  - perc-transaction-resp-time (p90) warn >= 1s fail >= 2s per test
  - error-rate warn >= 2% fail >= 5% per test
  - error-rate warn >= 5% per interval
variables:
- file:
    name: products
    path: data/list_of_products.csv
servers:
- name: mypc
  host: mypc.intranet.company.com
user_paths:
- name: MyUserPath
  actions:
    sla_profile: MySlaProfile
    steps:
    - request:
        url: http://www.company.com/select?name=${products.col_0}
    - think_time: 1s
    - request:
        server: mypc
        url: /valide
populations:
- name: MyPopulation
  user_paths:
  - name: MyUserPath
    distribution: 100%
scenarios:
- name: MyScenario
  populations:
  - name: MyPopulation
    constant_load:
      users: 10
