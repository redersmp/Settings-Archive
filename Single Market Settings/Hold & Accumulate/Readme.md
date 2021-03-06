## Hold & Accumulate
by Hojou

This is a simple SMS for PTMagic which will allow you to designate coins you intend to hold, while still accumulating according to your DCA settings.  Optionally, you can turn off DCA to just hold without any accumulation.

The trigger is designed to be true for ANY coin you add to the **"AllowedMarkets"** field -- any allowed coin that is under 50000% for the day.  You **MUST NOT** leave "AllowedMarkets" blank, or the SMS will be applied to all coins on the market.  If you have no coins you wish to hold, use a string that doesn't represent any particular coin (like xxx).

Unlike Profit Trailer, PTMagic doesn't know what market you are trading in, so you must always specify your base currency when using "AllowedMarkets" or "IgnoredMarkets".  [See the wiki](https://github.com/PTMagicians/PTMagic/wiki/settings.analyzer#allowedmarkets) for more information.

This should be added before any other SMS settings that have "StopProcessWhenTriggered": true, or placed in such a way to make sure other SMS settings don't change the settings it specifies.


````
      //---------------------
      //   HOLD & ACCUMULATE
      //---------------------
      {
        "SettingName": "Hold",
        "TriggerConnection": "OR",
        "StopProcessWhenTriggered": true,
        "AllowedMarkets": "xxxBTC",
        "Triggers": [
        {
                "MarketTrendName": "24h",
                "MarketTrendRelation": "Absolute",
                "MaxChange": 50000.0
        }
        ],
        "PairsProperties": {
                "DEFAULT_DCA_enabled": "false", // Disable DCA
		"DEFAULT_A_sell_value": 9999, // you must change the letter A to match your EMAGAIN setting
                "DEFAULT_take_profit_wait_time": 9999,  // Disable Take Profit
                "DEFAULT_take_profit_safety_arm": 9999, // Disable Take Profit Safety
                "DEFAULT_take_profit_safety_fire": 9998, // Disable Take Profit Safety
                "DEFAULT_trailing_stop_loss_trigger_arm": 9999, // Disable Trailing Stop
                "DEFAULT_trailing_stop_loss_trigger": 9998, // Disable Trailing Stop
        },
        "DCAProperties": {}
      },
````
