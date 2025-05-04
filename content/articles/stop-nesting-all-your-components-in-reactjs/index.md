+++
title = "Stop Nesting All Your Components in your ReactJS Apps"
description = "In ReactJS it's better to pass components as props rather than nesting everything. Here's how to do it!"
summary = "In ReactJS it's better to pass components as Props rather than nesting everything. Here's how to do it!"
tags = ["ReactJS"]
ShowPostNavLinks = false
+++
We can avoid tight coupling by using composition in our ReactJS apps.

I'll break down what that means and why it's generally a more robust and maintainable approach.

Imagine you're building a UI with various elements like containers, panels, and specific content within them.

## The "Render Everything" Approach (Less Ideal):

In this scenario, a container component might directly import and render all the specific content components it needs. For example:

```jsx
// ContainerComponent.jsx
import React from 'react';
import ProfileInfo from './ProfileInfo';
import UserActivityFeed from './UserActivityFeed';
import SettingsPanel from './SettingsPanel';

function ContainerComponent() {
  return (
    <div className="container">
      <ProfileInfo userId={123} />
      <UserActivityFeed currentUser={123} />
      <SettingsPanel onSave={handleSettingsSave} />
      {/* ... more specific components ... */}
    </div>
  );
}

export default ContainerComponent;

``` 

Here, ``ContainerComponent`` is tightly coupled to ``ProfileInfo``, ``UserActivityFeed``, and ``SettingsPanel``.


## The "Pass Components as Props" Approach (More Ideal):

Instead, we can make ``ContainerComponent`` more generic and flexible by accepting other components as props:


```jsx
// Layout.jsx (a more generic container)
import React from 'react';

function Layout({ header, sidebar, children, footer }) {
  return (
    <div className="app-layout">
      <header>{header}</header>
      <aside>{sidebar}</aside>
      <main>{children}</main>
      <footer>{footer}</footer>
    </div>
  );
}

export default Layout;

// Usage in a specific context:
import React from 'react';
import Layout from './Layout';
import ProfileInfo from './ProfileInfo';
import UserActivityFeed from './UserActivityFeed';
import SettingsPanel from './SettingsPanel';

function DashboardPage() {
  return (
    <Layout
      header={<h1>User Dashboard</h1>}
      sidebar={<SettingsPanel onSave={handleSettingsSave} />}
      children={
        <>
          <ProfileInfo userId={123} />
          <UserActivityFeed currentUser={123} />
        </>
      }
      footer={<p>&copy; 2025 My App</p>}
    />
  );
}

export default DashboardPage;
```

In this approach, ``Layout`` doesn't care what the ``header``, ``sidebar``, ``children``, or ``footer`` are. It simply knows where to render them. The ``DashboardPage`` then composes the layout by passing in the specific components it needs.

## Why is the "Pass as Props" approach better?

* __Increased Reusability:__ The ``Layout`` component becomes highly reusable. You can use it for different pages or sections of your application simply by passing different sets of components as props. You're not locked into a specific set of children.
* __Loose Coupling:__ The parent component (like ``Layout``) doesn't need to know the implementation details of the child components (``ProfileInfo``, ``UserActivityFeed``, etc.). This makes your codebase more modular and easier to maintain. Changes in a child component are less likely to break the parent.
* __Improved Flexibility:__ You can easily rearrange the structure of your UI by passing different components to different prop slots. For example, you could easily move the ``SettingsPanel`` to the main content area instead of the sidebar by just changing the props passed to ``Layout``.
* __Easier Testing:__ When testing the ``Layout`` component, you can pass in simple mock components as props, making your tests more focused and less reliant on the behavior of the actual child components.
* __Clearer Component Responsibility:__ Each component has a more focused responsibility. The container component is responsible for the overall structure, while the parent component using the container decides what content goes where.
* __Better Code Readability:__ The intent of the parent component becomes clearer. You can see exactly which components are being used within the container by looking at the props it receives.

## Common Patterns for Passing Components as Props:

* ``children`` __prop:__ This is a special prop that represents the components directly nested within a component's JSX tags. It's often used for layout components where you want to wrap other content.
* __Specific prop names:__ As seen in the ``Layout`` example (``header``, ``sidebar``, ``children``, ``footer``), you can define specific prop names to indicate where different components should be rendered.
* __Render Props:__ A function prop that a component uses to know what to render. This is a more advanced pattern that provides even greater flexibility for sharing functionality.


In essence, favoring composition over direct rendering leads to a more flexible, reusable, and maintainable React codebase. It allows you to build complex UIs by assembling smaller, independent components in a declarative way.

----

If you like help with this, [reach out to me!](https://clarity.fm/rajduggal/precall/free)
