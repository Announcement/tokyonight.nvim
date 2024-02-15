# usage

Set `$wt_settings` to the location of your windows terminal settings json.
Set `$scheme_dir` to the directory of the schemes you would like to load.

``` powershell
# read your wt settings
$wt_config = Get-Content $wt_settings | ConvertFrom-Json

# read your colorful scheme json files
$schemes = Get-ChildItem $scheme_dir/*.json | % { Get-Content $_ | Select-String -Pattern "^[^#]" | ConvertFrom-Json }

# install them to our virtual representation
$wt_config.schemes = $wt_config.schemes + $schemes

#render the settings file!
$wt_config | ConvertTo-Json -Depth 10 | set-clipboard
```

paste it back into your windows terminal settings from your clipboard and ur dun

optionally `out-file` but i like to look at it first make sure nothin goofy happened.
