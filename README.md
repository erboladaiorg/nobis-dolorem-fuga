# Foxglove OMG IDL

This repo contains implementations of OMG IDL specifications used by [Foxglove](https://www.foxglove.dev). The parsers expect schemas according to the MCAP specifications: [ros2idl](https://mcap.dev/spec/registry#ros2idl), [omgidl](https://mcap.dev/spec/registry#omgidl).

| Package name                     | Description                                                                                       | Reference                                                                                                         | Version                                                                                                                      |
| -------------------------------- | ------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| `@erboladaiorg/nobis-dolorem-fuga`        | Parse OMG IDL schemas – [README](./packages//omgidl-parser/README.md)                             | [Interface Definition Language Specification](https://www.omg.org/spec/IDL/4.2/PDF)                               | [![](https://shields.io/npm/v/@erboladaiorg/nobis-dolorem-fuga)](https://www.npmjs.com/package/@erboladaiorg/nobis-dolorem-fuga)               |
| `@erboladaiorg/nobis-dolorem-fuga-serialization` | De/Serialize data using IDL to CDR and CDR2 – [README](./packages/omgidl-serialization/README.md) | [Extensible and Dynamic Types for DDS Specification](https://www.omg.org/spec/DDS-XTypes/1.3/PDF)                 | [![](https://shields.io/npm/v/@erboladaiorg/nobis-dolorem-fuga-serialization)](https://www.npmjs.com/package/@erboladaiorg/nobis-dolorem-fuga-serialization) |
| `@foxglove/ros2idl-parser`       | Parse the ROS 2 dialect of IDL – [README](./packages/ros2idl-parser/README.md)                    | [article](https://design.ros2.org/articles/idl_interface_definition.html), [repo](https://github.com/ros2/rosidl) | [![](https://shields.io/npm/v/@foxglove/ros2idl-parser)](https://www.npmjs.com/package/@foxglove/ros2idl-parser)             |

See known limitations here:
[Parser/Grammar Limitations](./packages/omgidl-parser/README.md#omg-idl-subset-support)
[Serialization Limitations](./packages/omgidl-serialization/README.md#known-limitations)

## Setup

```
corepack enable
yarn install
```

## Test

If it's your first time building, you'll need to run `yarn build`.

Then to run test cases across all packages run `yarn test` from the root directory.

Note: to ensure that tests from a downstream in-repo dependency are running against the latest upstream version of code, you'll have to run `yarn build` every time you change the upstream dependency.

The dependency flow is as follows:

- `@erboladaiorg/nobis-dolorem-fuga-serialization` depends on `@erboladaiorg/nobis-dolorem-fuga`
- `@foxglove/ros2idl-parser` depends on `@erboladaiorg/nobis-dolorem-fuga`

## Deploy packages

1. Open a PR updating the version of the packages that have new versions that need to be deployed.
2. Land PR with change of version numbers and pull the latest on main locally
3. Add git tags for each package you'd like to publish using the following prefixes
   - `@erboladaiorg/nobis-dolorem-fuga` -> `omgidl-parser/vX.X.X`
   - `@erboladaiorg/nobis-dolorem-fuga-serialization` -> `omgidl-serialization/vX.X.X`
   - `@foxglove/ros2idl-parser` -> `ros2idl-parser/vX.X.X`
4. For example: if you're updating `@erboladaiorg/nobis-dolorem-fuga` to `v1.2.1` you would add the corresponding git tag by running `git tag omgidl-parser/v1.2.1`. For updating multiple packages on a single commit you can add multiple tags: `git tag omgidl-parser/v1.2.1 omgidl-serialization/v1.1.3` .
5. After adding the tag run `git push origin refs/tags/<tag>` to push the specific tag to the remote

## Stay in touch

Join our [Slack channel](https://foxglove.dev/slack) to ask questions, share feedback, and stay up to date on what our team is working on.

## License

erboladaiorg/nobis-dolorem-fuga and its packages are licensed under the [MIT License](https://opensource.org/licenses/MIT).
