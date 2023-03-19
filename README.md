# learn-test-everything

## GitHub Config
1. 自动签名
> 参考: https://stackoverflow.com/questions/15015894/git-add-signed-off-by-line-using-format-signoff-not-working

    ```shell
    1. cp .git/hooks/pre-commit-msg.sample  .git/hooks/pre-commit-msg

    2. 放开以下两行注释
       SOB=$(git var GIT_COMMITTER_IDENT | sed -n 's/^\(.*>\).*$/Signed-off-by: \1/p')
       git interpret-trailers --in-place --trailer "$SOB" "$COMMIT_MSG_FILE"
    ```
    这样在提交时候就会自动签名，其他的方式比如 `format.signoff true` **实测无用**
