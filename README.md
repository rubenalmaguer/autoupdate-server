# Autoupdate server for Electron apps

A simple release server for:

- [Pepino Viewer](https://github.com/rubenalmaguer/pepino-viewer) (Private)

## Endpoints

(electron-updater will append `/latest.yml`)

https://autoupdater.netlify.app/pepino-viewer/latest

## Serve locally

1. Install netlify cli globally

```
npm install netlify-cli -g
```

2. Run `netlify dev`

3. If using electron, add this to package.json:

```json
    "publish": [
      {
        "provider": "generic",
        "url": "https://autoupdater.netlify.app/pepino-viewer/latest",
        /* For local testing,
        use the url provided
        by netlify cli:
          "url": "http://127.0.0.1:8888/pepino-viewer/latest"
        */
      }
    ]
```

## Test

1. Downgrade app's version number in package.json

2. Install artificially-downgraded version

3. If autoupdates are turned on you should be prompted to update, else, use the menu to trigger a manual update.

## Create a release

Your endpoint's "latest" folder should contain these files created by electron-build:

- {your app}.exe (required)
- latest.yml (required)
- {your app}.exe.blockmap (nice-to-have)
- builder-debug.yml (maybe?)
- builder-effective-config.yaml (maybe?)

## References

https://gist.github.com/iffy/0ff845e8e3f59dbe7eaf2bf24443f104

https://github.com/davidterins/auto-update-electron-app
