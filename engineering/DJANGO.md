# Django Standards

These are things we've found to solve common issues an save lots of time.

## Client Cache Management

Include version string in static assets paths loaded from the client.

```
<script src="script.js?v={{ settings.VERSION }}"></script>
```

This is a wonderful catchall to prevent client cache issues that waste so much time.
