# @sudobility/superguide_types

Shared TypeScript type definitions for the Superguide API ecosystem.

## Installation

```bash
bun add @sudobility/superguide_types
```

Peer dependency: `@sudobility/types` must also be installed.

## Usage

```ts
import {
  History,
  HistoryCreateRequest,
  HistoryUpdateRequest,
  HistoryTotalResponse,
  successResponse,
  errorResponse,
  BaseResponse,
  NetworkClient,
} from "@sudobility/superguide_types";

const response = successResponse<History[]>(data);
const error = errorResponse("Something went wrong");
```

## Types

| Type | Description |
|------|-------------|
| `History` | Core data type: `id`, `user_id`, `datetime`, `value`, timestamps |
| `HistoryCreateRequest` | `{ datetime, value }` |
| `HistoryUpdateRequest` | `{ datetime?, value? }` |
| `HistoryTotalResponse` | `{ total }` |
| `BaseResponse<T>` | Standard API envelope (re-exported from `@sudobility/types`) |
| `NetworkClient` | HTTP client interface (re-exported from `@sudobility/types`) |

## Helpers

- `successResponse<T>(data)` -- wraps data in `BaseResponse<T>` with `success: true`
- `errorResponse(error)` -- wraps error string in `BaseResponse<never>` with `success: false`

## Development

```bash
bun run build          # Build dual ESM/CJS
bun run dev            # Watch mode
bun test               # Run Vitest tests
bun run typecheck      # TypeScript check
bun run lint           # ESLint
bun run verify         # All checks + build (use before commit)
```

## Related Packages

- **superguide_api** -- Backend API server (Hono + PostgreSQL)
- **superguide_client** -- API client SDK with TanStack Query hooks
- **superguide_lib** -- Business logic library with Zustand stores
- **superguide_app** -- Web application (React + Vite)
- **superguide_app_rn** -- React Native mobile app (Expo)

## License

BUSL-1.1
