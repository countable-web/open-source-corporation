# Dependency Strategy

This page covers dependency selection and management.

## Javascript Frameworks

Javascript frameworks are a big discussion and there isn't a nice answer IMO. The problem is our projects often live for 5 to 10 years. Javascript frameworks do not.

We do use Angular a lot. React is acceptable, but Preact is better for 2 reasons. 1. it's identical but smaller. 2. it discourages excessive plugin dependencies.

The problem of using the "framework of the day" is that javascript frameworks only grow for about 3 years and then they always slowly die. jQuery is slowly fading away now, Angular has peaked and is losing market share to React. React is close to peaking and is starting to lose to Vue. By next year, Vue will be more popular than either angular and react and it's a better framework so the answer is to use Vue, right?

The problem is, we build 5 apps in Vue, and then something else replaces it in 2 to 3 years, and we now have to support old apps in so many frameworks with dying communities. I think the best defense we have against this is:

1) Use Django, and don't build single page applications most of the time. Django is already very old but still going strong and growing over time.
2) For small interactive front end pieces, something like Preact or Riot is pretty ideal because they're tiny. They're so small that if they go out of support we can fork them. Also, they're so simple that a much smaller portion of your app needs to be coupled strongly to the framework. It's easier to port out of them. The only really helpful feature in React and Angular is the 2 way dom binding. The rest of their features are of very dubious value. So, by using a library like Riot that only has just that, a 2 way dom binding, you have way less risk associated with the dependency. Less of your app depends on it. Lastly, you get better performance since they're small, as a nice bonus.
3) When you really need a single page app, it may make sense to use the framework of the day (Vue, or React currently). We can't always avoid this, but we can try to minimize it most of the time.
4) Avoid framework-specific sub-dependencies like react-hamburger-menu or angularstrap. Framework plugins are the first thing to die when the framework dies. Use dependency-free, specific purpose plugins if you need any.
