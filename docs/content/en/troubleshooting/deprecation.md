---
title: Deprecation
description: The Hugo project follows a formal and consistent process to deprecate functions, methods, and configuration settings.
categories: []
keywords: []
---

When a project _deprecates_ something, they are telling its users:

1. Don't use Thing One anymore.
1. Use Thing Two instead.
1. We're going to remove Thing One at some point in the future.

[reasons for deprecation]: https://en.wikipedia.org/wiki/Deprecation

Common [reasons for deprecation]:

- A feature has been replaced by a more powerful alternative.
- A feature contains a design flaw.
- A feature is considered extraneous, and will be removed in the future in order to simplify the system as a whole.
- A future version of the software will make major structural changes, making it impossible or impractical to support older features.
- Standardization or increased consistency in naming.
- A feature that once was available only independently is now combined with its co-feature.

After the project team deprecates something in code, Hugo will:

1. Log an INFO message for 3 minor releases[^1]
1. Log a WARN message for another 12 minor releases
1. Log an ERROR message and fail the build thereafter

The project team will:

1. On the deprecation date, update the documentation with a note describing the deprecation and any relevant alternatives.
1. Remove the code six or more minor releases after Hugo begins logging ERROR messages and failing the build. At that point, Hugo will throw an error, but the error message will no longer mention the deprecation.
1. Remove the corresponding documentation two years after the deprecation date.

To see the INFO messages, you must use the `--logLevel` command line flag:

```text
hugo --logLevel info
```

To limit the output to deprecation notices:

```text
hugo --logLevel info | grep deprecate
```

Run the above command every time you upgrade Hugo.

[^1]: For example, v0.1.1 => v0.2.0 is a minor release.
