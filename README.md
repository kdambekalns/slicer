# slicer

_Some code to keep read-only package repositories updated._

This is inspired by https://github.com/dflydev/dflydev-git-subsplit-github-webhook, thanks!

## Configuration

See https://github.com/dflydev/dflydev-git-subsplit-github-webhook#configuration, the format is the same. Only
`allowed-ips` is not supported, since slicer is intended to be run in Jenkins and that has ways to secure the
request.

One addition is the `allowedRefsPattern` that can be given per project. If it does not match an incoming `ref`
in the payload, processing of the split is skipped.

## Setting up Jenkins

* Create parameterized job
* Have it clone slicer
* Add a string parameter called "payload"
* Add a shell build step running `php slicer.php "${payload}"`
