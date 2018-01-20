# Django Standards

These are things we've found to solve common issues an save lots of time.

## Client Cache Management

Include version string in static assets paths loaded from the client.

```
<script src="script.js?v={{ settings.VERSION }}"></script>
```

This is a wonderful catchall to prevent client cache issues that waste so much time.

## Use LTS Django

Use the long term support version of Django, ideally the latest one available at any given time.

## Read 2 Scoops of Django

This book contains a lot of great practices, which we _almost_ universally agree with.
