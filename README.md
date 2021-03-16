# heroku-pdftk-buildpack
buildpack with pdftk binaries, based on https://github.com/fxtentacle/heroku-pdftk-buildpack

## How to build new version yourself

Set `tarball_url` to the desired pdftk version in `scripts/build.sh`

Then run

```
git clone git@github.com:milopets/heroku-pdftk-buildpack.git

heroku create
heroku stack:set heroku-18
heroku buildpacks:set https://github.com/milopets/heroku-buildpack-apt
heroku buildpacks:set heroku/ruby

git push heroku main
```

This will trigger binaries build process on heroku, it can be observerd in logs.

Once it finishes:

* go to the application url and download the `pdftk.zip` file.
* unpack it locally
* copy `libgcj.so.17` and `pdftk` binary into this project `binaries-$STACK` folder
* call `chmod +x` on both files
* commit and push the repository

Once binaries are commited and pushed add this buildpack to your application.





