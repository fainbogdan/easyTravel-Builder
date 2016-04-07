# easyTravel-Builder

This project builds easyTravel deployment artefacts of the [Dynatrace easyTravel](https://community.dynatrace.com/community/display/DL/Demo+Applications+-+easyTravel) demo application for the following components:

## Application Components

| Component   | Description
|:------------|------------
| repository  | A pre-populated travel database (MongoDB) as `easyTravel-mongodb-db.tar.gz`.
| backend     | The easyTravel Business Backend (Java) as `backend.war`
| frontend    | The easyTravel Customer Frontend (Java) as `frontend.war`.
| loadgen     | A synthetic UEM load generator (Java) as `uemload.jar` plus dependencies in `loadgen.tar.gz`.

## How to build easyTravel?

### Option A: build-easytravel.sh

The `build-easytravel.sh` script builds easyTravel deployment artefacts into a directory `build` inside your current working directory, by default. You can override the default behavior by providing the following *environment variables* to the script:

| Environment Variable  | Defaults                    | Description
|:----------------------|:----------------------------|:-----------
| ET_SRC_URL            | https://s3.amazonaws.com/easytravel/dT63/easyTravel-2.0.0.2217-src.zip | A URL to an easyTravel source distribution .zip file.
| ET_BUILD_HOME         | ./build                     | A directory to contain the easyTravel deployment artefacts.
| ET_BB_BUILD_HOME      | ./backend                   | A directory under `${ET_BUILD_HOME}` to contain the easyTravel Business Backend deployment artefact (the artefact will be located in `${ET_BUILD_HOME}/${ET_BB_BUILD_HOME}`.
| ET_CF_BUILD_HOME      | ./frontend                  | A directory under `${ET_BUILD_HOME}` to contain the easyTravel Customer Frontend deployment artefact (the artefact will be located in `${ET_BUILD_HOME}/${ET_CF_BUILD_HOME}`.
| ET_LG_BUILD_HOME      | ./loadgen                   | A directory under `${ET_BUILD_HOME}` to contain the easyTravel UEM load generator deployment artefact (the artefact will be located in `${ET_BUILD_HOME}/${ET_LG_BUILD_HOME}`.

#### Example: create deployment artefacts in `./build`:

```
./build-easytravel.sh
```

#### Example: create deployment artefacts in `./build` and no sub-folders:

```
ET_BB_BUILD_HOME=. \
ET_CF_BUILD_HOME=. \
ET_LG_BUILD_HOME=. \
./build-easytravel.sh
```

#### Example: create deployment artefacts in `.` and no sub-folders:

```
ET_BUILD_HOME=. \
ET_BB_BUILD_HOME=. \
ET_CF_BUILD_HOME=. \
ET_LG_BUILD_HOME=. \
./build-easytravel.sh
```

### Option B: `build-easytravel-in-docker.sh`

Use `build-easytravel-in-docker.sh` if you want to build easyTravel deployment artefacts in a build environment that runs in Docker, so you don't have to set up your own. Deployment artefacts can be found in a directory `build` inside your current working directory. You can override the default behavior by providing the following *environment variables* to the script:

| Environment Variable  | Defaults                    | Description
|:----------------------|:----------------------------|:-----------
| ET_SRC_URL            | "https://s3.amazonaws.com/easytravel/dT63/easyTravel-2.0.0.2217-src.zip" | A URL to an easyTravel source distribution.
| ET_BUILD_HOME         | ./build                     | A directory to contain the easyTravel deployment artefacts under the current working directory.
| ET_BB_BUILD_HOME      | ./backend                   | A directory under `${ET_BUILD_HOME}` to contain the easyTravel Business Backend deployment artefact (the artefact will be located in `${ET_BUILD_HOME}/${ET_BB_BUILD_HOME}`.
| ET_CF_BUILD_HOME      | ./frontend                  | A directory under `${ET_BUILD_HOME}` to contain the easyTravel Customer Frontend deployment artefact (the artefact will be located in `${ET_BUILD_HOME}/${ET_CF_BUILD_HOME}`.
| ET_LG_BUILD_HOME      | ./loadgen                   | A directory under `${ET_BUILD_HOME}` to contain the easyTravel UEM load generator deployment artefact (the artefact will be located in `${ET_BUILD_HOME}/${ET_LG_BUILD_HOME}`.

#### Example: create deployment artefacts in `./build`:

```
./build-easytravel-in-docker.sh
```

#### Example: create deployment artefacts in `./build` and no sub-folders:

```
ET_BB_BUILD_HOME=. \
ET_CF_BUILD_HOME=. \
ET_LG_BUILD_HOME=. \
./build-easytravel-in-docker.sh
```

#### Example: create deployment artefacts in `.` and no sub-folders:

```
ET_BUILD_HOME=. \
ET_BB_BUILD_HOME=. \
ET_CF_BUILD_HOME=. \
ET_LG_BUILD_HOME=. \
./build-easytravel-in-docker.sh
```

## License

Licensed under the MIT License. See the LICENSE file for details.