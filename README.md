                ┌─────────────────────┐
                │     CLI / User      │
                └──────────┬──────────┘
                           │
                           ▼
                ┌─────────────────────┐
                │  React + Ink CLI    │
                └──────────┬──────────┘
                           │
                           ▼
                ┌─────────────────────┐
                │      AI SDK         │
                │       `ai`          │
                └──────────┬──────────┘
                           │
                 ┌─────────┴──────────┐
                 ▼                    ▼
          OpenAI provider       Other provider
        @ai-sdk/openai          e.g. Anthropic
                 │
                 ▼
             LLM / Agent
                 │
        ┌────────┼────────┐
        ▼        ▼        ▼
      Shell    Files    Other tools
        │
        ▼
     shelljs

                 │
                 ▼
          Laminar / LMNR
       tracing + evaluation
