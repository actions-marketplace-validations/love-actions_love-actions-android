# love-actions-android

## About

Github Action for building & deploying Android `.apk` and `.abb` packages of a [LÖVE](https://love2d.org/) framework based game.

### Related actions

See related actions below:

[Love actions bare package](https://github.com/marketplace/actions/love-actions-bare-package)

## Quick example

```yaml
- name: Build love android
  id: build-love
  uses: 26F-Studio/love-actions-android@v0.0.8-alpha
  with:
    app-name: "My Love Game"
    bundle-id: "org.love2d.my_game"
    keystore-alias: ${{ secrets.ANDROID_KEYSTORE_ALIAS }}
    keystore-base64: ${{ secrets.ANDROID_KEYSTORE_BASE64 }}
    keystore-key-password: ${{ secrets.ANDROID_KEYSTORE_KEYPASSWORD }}
    keystore-store-password: ${{ secrets.ANDROID_KEYSTORE_STOREPASSWORD }}
    love-package: "./game.love"
    resource-path: "./assets/android/dev/res"
    version-string: "2.3.4"
    version-code: 234
    output-folder: "./dist"
```

## All inputs

| Name                      | Required | Default                | Description                                                  |
| :------------------------ | -------- | ---------------------- | ------------------------------------------------------------ |
| `app-name`                | `false`  | `"LÖVE App"`           | App display name, used in `app/src/main/AndroidManifest.xml` |
| `bundle-id`               | `false`  | `"org.love2d.android"` | App bundle id, used in `app/build.gradle`                    |
| `icon-specifier`          | `false`  | `"@mipmap/icon"`       | App icon specifier used in `app/src/main/AndroidManifest.xml` |
| `keystore-alias`          | `false`  | `""`                   | Signing keystore's alias, won't build release packages if not specified |
| `keystore-base64`         | `false`  | `""`                   | Signing keystore's content in `base64` string, won't build release packages if not specified |
| `keystore-key-password`   | `false`  | `""`                   | Signing keystore's key password, won't build release packages if not specified |
| `keystore-store-password` | `false`  | `""`                   | Signing keystore's store password, won't build release packages if not specified |
| `love-package`            | `false`  | `"./game.love"`        | `.love` game package file path                               |
| `resource-path`           | `true`   | `""`                   | Path to the android resources folder, would copy all contents to `app/src/main/res` exclude top folder |
| `version-string`          | `false`  | `"1.0.0"`              | App version string no more than 3 numbers, used in `app/build.gradle` |
| `version-code`            | `false`  | `"100"`                | Numeric app version code , used in `app/build.gradle`       |
| `output-folder`           | `false`  | `"./build"`            | Built packages output folder                                 |

## All outputs

| Name            | Example                                                      | Description                                                  |
| :-------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `package-paths` | `./build/app-embed-record-debug.apk ./build/app-embed-record-release.apk` | built packages' paths in a bash-style list relative to the repository root, separated by spaces |
