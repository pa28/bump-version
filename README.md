# bump-version
Bump the version number of a cmake project. This repository is designed to be used as a submodule in a CMake project repository
to add commands to manage the project version number.

See [dummy-cmake-project](https://github.com/pa28/dummy-cmake-project) for
an example.

## Synopsis

In the top level of your CMake project:
```bash
git submodule add https://github.com/pa28/bump-version.git [<dirname>]
```

In your `CMakeLists.txt` file ensure you have a `VERSION` specified in your
`progject()` statement, and add this:
```cmake
ADD_SUBDIRECTORY(<dirname>)
```

## Commands
```bash
${CMAKE_CURRENT_BINARY_DIR}/<dirname>/current_version
```
Returns the current version, without an new-line appended.

```bash
${CMAKE_CURRENT_BINARY_DIR}/<dirname>/bump_version -l <version-level> [-m "commit message"] [-M "tag message"] [-t] [-p] [-T]
```
 * **version-level**: the version level to bump, case insensitive.
  May be one of major, minor, patch or tweak. Required
 * **commit message**: the commit message. Optional, if omitted the commit
 message will be "<current-version> => <new-version> <version-level>"
 * **tag message**: the tag message. Optional, if ommitted the tag message
 defaults to the commit message.
 * **-t**: Set a commit tag to the new version.
 * **-p**: Push the changes (and tag if set) to the current branch.
 * **-T**: Try only. Displays what the command will do, but takes no action.

## Make Targets

The following `make` targets are defined:
 * **bump_tweak**: equivalent to `bump_version -l tweak -t -p`
 * **bump_patch**: equivalent to `bump_version -l patch -t -p`
 * **bump_minor**: equivalent to `bump_version -l minor -t -p`
 * **bump_major**: equivalent to `bump_version -l major -t -p` 