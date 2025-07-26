graph TD
  %% Section: Telemetry & Monitoring (Blue)
  subgraph Azure_Cloud[Deployed on Azure]
    A1[Application] --> A2[OTEL Collector]
    A1 --> A3[Cloud Gateway]
    A2 --> A3
    A3 --> A4[Span Server]
    A3 --> A5[Metric Streamer]
    A3 --> A6[API Management]
    A6 --> A7[Application Gateway]
    A7 --> A8[Application Firewall]
    A8 -->|Send to| R1[PAC Tigervy]

    A4 --> A9[API]
    A5 --> A9
    A9 --> A10[Load Balancer]
    A10 --> A11[Express Route WE]
    A10 --> A9

    A9 --> A12[OpenTelemetry Dependencies]
    A9 --> A13[Grafana]
    A13 --> A14[API Dashboard]

    A9 --> A15[Span UI Server]
    A15 --> A16[Zipkin UI]
  end

  %% Section: Portal Stack (Red)
  subgraph Portal_Infra[Deployed on Premises]
    R2[Application] --> R3[Cloud Gateway]
    R3 --> R4[PAC Tigervy]
    R3 --> R5[Portal API]
    R5 --> R6[K8s Ingress]
    R6 --> R7[Portal UI]
    R7 --> R8[Administrators]
    R4 --> R7
    R4 --> R9[Users]
  end

  %% Legend Info (can be visualized separately in a diagram)
  %% You can represent legend separately in a note or use tooltips in real diagrams.