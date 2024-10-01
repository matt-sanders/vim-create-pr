# vim-create-pr

Open link to new pull request with provided/current branch directly from (neo)vim.

Works with `Github`, `Bitbucket` and `Gitlab` out of the box. Can be [extended](#customization).

## Installation

Using [lazy](https://github.com/folke/lazy.nvim)

```lua
{ 'mattsanders/vim-create-pr' }
```

## Usage

Use one of the following commands:

- `:PR` Opens a PR for the current branch
- `:PR target_name` Opens a PR for the current branch comparing the target branch
- `:PR target_name branch_name` Opens a PR for the selected branch comparing the target branch

Branch names can be autocompleted.

If you are using [vim-twiggy](https://github.com/sodapopcan/vim-twiggy),
select a branch from list and press `pr`.

If you want to open only repository page in browser, run this:

```
:RepoPage
```

## Customization

### Additional git services

To add your custom git service to the list, add `g:create_pr_git_services`
variable to your vimrc, using example below:

```vimL
let g:create_pr_git_services = {
\ 'my.gitlab.com': 'https://my.gitlab.com/{{owner}}/{{repository}}/merge_requests/new?merge_request[source_branch]={{branch_name}}'
\ }

let g:create_pr_with_target_git_services = {
\ 'my.gitlab.com': 'https://my.gitlab.com/{{owner}}/{{repository}}/merge_requests/new?merge_request[source_branch]={{branch_name}}&merge_request[target_branch]={{target_branch_name}}'
\ }
```

Make sure key name (`my.gitlab.com` in example above) is part of the string returned from this command:

```
git config --get remote.origin.url
```

### Custom browser

Default browser is used by default, when available (`xdg-open`, `open` on mac).
To use custom browser, add `g:create_pr_browser` to your vimrc with executable name.

Example:

```vimL
let g:create_pr_browser = 'firefox'
```
