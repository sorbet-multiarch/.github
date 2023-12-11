# Welcome to sorbet-multiarch
Community built Sorbet gems that support linux/arm64 (devcontainers on macOS)!

To use these gems, just change your `Gemfile`:
```
source 'https://gem.fury.io/sorbet-multiarch/' do
  gem 'sorbet-static'
  gem 'sorbet'
end
```

## What problem does this solve?
[Sorbet](https://github.com/sorbet/sorbet/) provides type checking for Ruby.
Sorbet includes a compiled binary in the `sorbet-static` gem used during development.
At the time of writing, this binary is not natively built for any arm64 platform.
Sorbet has [a long running issue]([url](https://github.com/sorbet/sorbet/issues/4119)) tracking linux/arm64 support.

sorbet-multiarch provides community builds of Sorbet **with native support for linux/arm64**, built in [CircleCI](https://app.circleci.com/pipelines/github/sorbet-multiarch/sorbet-builder?filter=all) and hosted on [Gemfury](https://gemfury.com/sorbet-multiarch).

## How are the gems built?
The process is straight forward:
1. The `sorbet-static` is [patched]([url](https://github.com/sorbet-multiarch/sorbet-builder/blob/main/fix-arm64-build.patch)) and built for linux/arm64 in CircleCI.
2. The `sorbet-static` gem is uploaded to Gemfury.
3. The other gems for that Sorbet version are copied from Rubygems to Gemfury.

A [nightly build]([url](https://app.circleci.com/pipelines/github/sorbet-multiarch/sorbet-builder)) will run, building and publishing the latest Sorbet version.

See all the [supported versions]([url](https://gemfury.com/sorbet-multiarch/ruby:sorbet-static)). If you need a version not supported, just [start a discussion](https://github.com/orgs/sorbet-multiarch/discussions).

## Components
Several repositories are involved:
1. [sorbet-build-image-builder](https://github.com/sorbet-multiarch/sorbet-build-image-builder) - builds the sorbet-image-builder Docker image **from upstream source**.
2. [sorbet-builder](https://github.com/sorbet-multiarch/sorbet-builder) - builds the `sorbet-static` gem for linux/arm64 **from upstream source**.

This project utilizes the generous free tiers from some amazing companies:
1. [GitHub](https://github.com) for source code and Docker image hosting.
2. [CircleCI](https://circleci.com/) for continuous integration (specifically Linux arm64 compute!).
3. [Gemfury](https://gemfury.com/) for gem artifact repository hosting.

## Disclaimer
This project is not affiliated with either [Sorbet](https://github.com/sorbet/) or [Stripe](https://stripe.com/).
