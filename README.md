# teslatariff
Sample YAML for pushing an arbitrary complex bespoke tariff to HA Powerwalls via Teslemetry
You will require a Teslemetry account, and the Teslemetry HA integration.
This works with the Tesla Fleet HA integration.  Other Tesla API integrations may require tweaks to the code.
Notes:
- enter your Teslemetry HA ID in the third line
- update OFF_PEAK, PEAK and MID_PEAK to the rates in £ for each rate type
- update the periods blocks to allocate all time periods to one of the rate types
- rows after sell_tariff refer to export rates; rows above that are import rates

action: teslemetry.time_of_use
data:
  device_id: ENTER YOUR 32-HEX-DIGIT TESLEMETRY HA ID HERE
  tou_settings:
    tariff_content_v2:
      code: UK-CUSTOM-VARIABLE-1
      name: Export promotion
      utility: Custom
      currency: GBP
      daily_charges:
        - name: Charge
          amount: 0
      demand_charges:
        ALL:
          rates:
            ALL: 0
      daily_demand_charges: {}
      monthly_charges: 0
      monthly_minimum_bill: 0
      min_applicable_demand: 0
      max_applicable_demand: 0
      energy_charges:
        ALL:
          rates:
            ALL: 0
        Season1:
          rates:
            OFF_PEAK: 0
            PEAK: 3
            MID_PEAK: 3
      seasons:
        Season1:
          fromMonth: 1
          fromDay: 1
          toMonth: 12
          toDay: 31
          tou_periods:
            OFF_PEAK:
              periods:
                - fromDayOfWeek: 0
                  toDayOfWeek: 6
                  fromHour: 23
                  fromMinute: 0
                  toHour: 0
                  toMinute: 0
                - fromDayOfWeek: 0
                  toDayOfWeek: 6
                  fromHour: 0
                  fromMinute: 0
                  toHour: 6
                  toMinute: 0
                - fromDayOfWeek: 0
                  toDayOfWeek: 6
                  fromHour: 16
                  fromMinute: 0
                  toHour: 23
                  toMinute: 0
            PEAK:
              periods:
                - fromDayOfWeek: 0
                  toDayOfWeek: 6
                  fromHour: 6
                  fromMinute: 0
                  toHour: 13
                  toMinute: 0
            MID_PEAK:
              periods:
                - fromDayOfWeek: 0
                  toDayOfWeek: 6
                  fromHour: 13
                  fromMinute: 0
                  toHour: 16
                  toMinute: 0
      sell_tariff:
        name: Export promotion
        utility: Custom
        currency: GBP
        code: ""
        daily_charges:
          - name: Charge
            amount: 0
        demand_charges:
          ALL:
            rates:
              ALL: 0
        daily_demand_charges: {}
        monthly_charges: 0
        monthly_minimum_bill: 0
        min_applicable_demand: 0
        max_applicable_demand: 0
        energy_charges:
          ALL:
            rates:
              ALL: 0
          Season1:
            rates:
              OFF_PEAK: 0
              PEAK: 0.15
              MID_PEAK: 2
        seasons:
          Season1:
            fromMonth: 1
            fromDay: 1
            toMonth: 12
            toDay: 31
            tou_periods:
              OFF_PEAK:
                periods:
                  - fromDayOfWeek: 0
                    toDayOfWeek: 6
                    fromHour: 23
                    fromMinute: 0
                    toHour: 0
                    toMinute: 0
                  - fromDayOfWeek: 0
                    toDayOfWeek: 6
                    fromHour: 0
                    fromMinute: 0
                    toHour: 6
                    toMinute: 0
              PEAK:
                periods:
                  - fromDayOfWeek: 0
                    toDayOfWeek: 6
                    fromHour: 6
                    fromMinute: 0
                    toHour: 13
                    toMinute: 0
                  - fromDayOfWeek: 0
                    toDayOfWeek: 6
                    fromHour: 16
                    fromMinute: 0
                    toHour: 23
                    toMinute: 0
              MID_PEAK:
                periods:
                  - fromDayOfWeek: 0
                    toDayOfWeek: 6
                    fromHour: 13
                    fromMinute: 0
                    toHour: 16
                    toMinute: 0
