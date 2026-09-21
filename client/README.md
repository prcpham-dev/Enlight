# Frontend

The Next.js application runs separately from the Python server. Start the
server from `server/` with:

```text
uvicorn media_engine.api:create_app --factory
```

Start the client from `client/` with:

```text
npm install
npm run dev
```

Open `http://localhost:3000`. The client API client uses
`http://localhost:8000` by default; set `NEXT_PUBLIC_SERVER_URL` if the server
runs elsewhere.

`/` is the live camera view. Start `python -m media_engine --camera 0` from
`server/` to publish frames to the API. The browser reconnects automatically
and reports unavailable or stale feeds. The focused person's saved details
appear below the image, and bounding boxes follow the same displayed frame.

`/memories` lists actual saved text notes by file modification date; note edits
retain their IDs and paths. Text notes belong to one enrolled person at a time.
`/person/[id]` shows saved facts, notes, name correction, and evidence-backed
shared events. Person names may be null while automatic naming gathers evidence.
See [Stages 7–12 checks](../server/STAGE_7_TO_12_CHECKS.md) for the browser
and graph review procedure.
