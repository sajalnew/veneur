# DogStatsD

This is an area of Veneur that may be refactored in the future as we find better ways to be sink agnostic.

Veneur can parse Datadog's [DogStatsD](https://docs.datadoghq.com/developers/dogstatsd/). After doing so, it must use an intermediary representation of the various primitives — metrics, events and service checks — that Datadog deals with. Since Veneur supports many sinks and tries to be agnostic, there's some mapping to be done.

The `protocol.go` in this directory defines some tags that are used as intermediary keys when passing events and service checks on to sinks in the form of an [SSF Sample](https://github.com/stripe/veneur/tree/master/ssf). Interested sinks will use these tags to compose whatever format is necessary to represent an equivalent of an event of service check, if applicable, in that sink's target.

You can find examples of this in the [SignalFx sink](https://github.com/stripe/veneur/tree/master/sinks/signalfx) which handles events.
