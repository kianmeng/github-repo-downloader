# github-repo-downloader

This tool allows you to download all the public repositories of GitHub users and
organizations. It doesn't require any access tokens to fetch repositories;
instead, it uses web scraping to retrieve data.

Keep in mind that if there are any changes to the website's HTML structure, it
might affect the tool's functionality.

## basic usage

Build the program:

```sh
go build -v
```

Specify the repositories to fetch for users or organization using the formats
`org:organization-name` or `user:user-name`. You can specify more than one org
or user:

```sh
./repo-downloader user:boreec org:golang user:octocat org:rust-lang
```

## using flags

There are available flags to customize the tool's behavior. Under the hood,
`flag` package is used to parse the arguments/options/flags. Thus, it is
required that all flags precede the arguments:

```sh
./repo-downloader --flag1 --flag2 ARG1 ARG2 [...]
```

For a list and a short description of the flags, use `-h`.

### --dry-run

You can provide the flag `--dry-run` for displaying the fetchable repositories
without actually cloning them:

```sh
./repo-downloader --dry-run user:octocat
```

### --debug
You can provide the flag `--debug` for displaying additional information
regarding what is happening under the hood:

```sh
./repo-downloader --dry-run --debug user:octocat
```

### --output-directory

By default, the repositories will be cloned in a local folder `cloned-repos`
(created if not existing already). In that folder, every target will have its
own subfolder with its repositories.

The local folder can be changed using the floag `--output-directory`:

```sh
./repo-downloader --output-directory="mydir" user:octocat
```
