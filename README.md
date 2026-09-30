# Reddit RSS Bridge

A small, self-hosted bridge that retrieves public subreddit submissions using Reddit's authenticated Data API and exposes them as RSS/Atom feeds for consumption by a personal RSS reader.

## Purpose

Reddit RSS Bridge is intended for personal, non-commercial use.

The project exists to allow a single user to continue following public Reddit communities through a self-hosted RSS reader. It periodically retrieves new public submissions from a configured set of subreddits and converts those submissions into standard RSS/Atom feeds.

The generated feeds are intended to be consumed by [Tiny Tiny RSS (tt-rss)](https://tt-rss.org/).

## Architecture

```text
Reddit Data API
      |
      | OAuth authenticated, read-only requests
      v
Reddit RSS Bridge
      |
      | RSS / Atom
      v
Tiny Tiny RSS
```

The bridge will run on a private, self-hosted server and will be used by a single user.

## Reddit API Usage

The application will:

- Authenticate using Reddit's supported OAuth mechanism.
- Retrieve public submissions from a small, explicitly configured set of subreddits.
- Operate at a low request frequency appropriate for a personal RSS reader.
- Use read-only API access.
- Identify itself using an appropriate application User-Agent.
- Respect Reddit API rate limits and applicable API requirements.

The application will **not**:

- Submit posts or comments.
- Vote on content.
- Send messages.
- Perform moderation actions.
- Access private messages or private subreddit content.
- Scrape Reddit pages to circumvent API restrictions.
- Attempt to bypass Reddit rate limits or other access controls.

## Data Handling

Only the data required to construct the RSS/Atom feeds will be retrieved.

The bridge is designed to use a short-lived local cache rather than maintain a permanent archive of Reddit content. Cached data will be refreshed periodically and retained only as needed to provide reliable RSS feeds.

The application is not intended to redistribute or sell Reddit data, provide a public Reddit data service, perform user profiling or analytics, or use Reddit content for AI/ML model training.

Tiny Tiny RSS is responsible for managing items after they have been delivered through the generated feed.

## Scope

This project is:

- Single-user
- Personal
- Non-commercial
- Self-hosted
- Read-only
- Intended only to access public subreddit submissions

It is not intended to be offered as a hosted or public service.

## Project Status

This project is currently in initial development. Reddit Data API access is being requested before implementation so that development and testing can use Reddit's supported authenticated API rather than undocumented or unauthenticated endpoints.

## Planned Feed Format

A configured subreddit will be exposed as a standard RSS or Atom feed, for example:

```text
/r/selfhosted  ->  /r/selfhosted.xml
/r/sysadmin    ->  /r/sysadmin.xml
/r/apple       ->  /r/apple.xml
```

These endpoints can then be subscribed to from any compatible RSS reader.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
