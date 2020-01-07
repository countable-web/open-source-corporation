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

## Patterns

### Views

We generally use function based views (FBV) instead of class based views (CBV) at Countable. When using Django Rest Framework (DRF), this is an exception and we prefer CBV. Please do use DRF for substantial rest API work.

Avoid unnecessary nesting.
```
#unnecessary nesting:
def view(request):
    if 'x' in request.GET:
        if (another check):
            return HttpResponse(...)
# better
def view(request):
    if 'x' not in request.GET:
        return Http400(...)
    if not another check:
        return Http400(...)
    return HttpResponse(...)
```
