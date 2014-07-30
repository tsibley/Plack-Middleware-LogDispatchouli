# NAME

Plack::Middleware::LogDispatchouli - Uses Log::Dispatchouli to configure the PSGI logger

# SYNOPSIS

    use Log::Dispatchouli;
    my $logger = Log::Dispatchouli->new(...);

    builder {
        enable "LogDispatchouli", logger => $logger;
        $app;
    }

    # or to make it even easier...
    builder {
        enable "LogDispatchouli", logger => {
            ident     => 'MyApp',
            facility  => 'daemon',
            to_stdout => $ENV{PLACK_ENV} eq "development",
            debug     => $ENV{PLACK_ENV} eq "development",
        };
        $app;
    }

# DESCRIPTION

Plack::Middleware::LogDispatchouli is a [Plack::Middleware](https://metacpan.org/pod/Plack::Middleware) component that
allows you to use [Log::Dispatchouli](https://metacpan.org/pod/Log::Dispatchouli) to configure the logging object,
`psgix.logger`.

# CONFIGURATION

- logger

    [Log::Dispatchouli](https://metacpan.org/pod/Log::Dispatchouli) object to send logs to or a hashref of parameters to pass
    to ["new" in Log::Dispatchouli](https://metacpan.org/pod/Log::Dispatchouli#new).

# AUTHOR

Thomas Sibley <trsibley@uw.edu>

# COPYRIGHT

Copyright 2014- Mullins Lab, Department of Microbiology, University of
Washington

This module is based on [Plack::Middleware::LogDispatch](https://metacpan.org/pod/Plack::Middleware::LogDispatch).

# LICENSE

This library is free software; you can redistribute it and/or modify
it under the same terms as Perl itself.

# SEE ALSO

[Log::Dispatchouli](https://metacpan.org/pod/Log::Dispatchouli)

[Plack::Middleware::LogDispatch](https://metacpan.org/pod/Plack::Middleware::LogDispatch)
