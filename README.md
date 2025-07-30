flowchart LR
    A["SNS"] -- Subscription --> B["Queue1"]
    B --> C("Debounce Handler")
    subgraph Debouncer
        C -- dedeupId+TTL --> D["Cache"]
        C -- Send+Delay --> E["Queue2"]
    end
    E -- Receive --> F["Handler"]

    B@{ shape: h-cyl}
    D@{ shape: cyl}
    E@{ shape: h-cyl}
