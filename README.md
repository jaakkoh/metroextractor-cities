metroextractor-cities
=====================
![Build Status](https://circleci.com/gh/mapzen/metroextractor-cities.png?circle-token=83dc13d4097b378ad6ba101b226118fda9e03844)

Description
-----------
* cities.json defines bounding boxes for various metro areas, which are used by [chef-metroextractor](https://github.com/mapzen/chef-metroextractor)
to produce weekly extracts.

Pull Request Overview
----------------------
You need to perform the following tasks for us to accept a pull request:

* update cities.json with your changes. Do not modify cities.geojson, it will be generated automatically when your pull request is merged.
*  run the included tests, which will validate:
  * the syntax of the json
  * that the bounding boxes being sumbitted are valid
  * that the bounding boxes for cities all fall within their encompassing upper level bounding box (e.g. north_america)
* the top/left/bottom/right bbox parameters should be carried out to the thousandths (three digits to the right of the decimal)

If you're unable to run the test suite locally, you can submit a pull request, but if the specs fail there will be a delay in getting your request resolved.

If in doubt, just submit an issue with your request rather than a pull request.

Running Tests
-------------
You will need to have a Ruby 2.x environment, then simply:

```
bundle install
bundle exec rake
```

Passing tests will look similar to the following:

```
Preparing sandbox
rm -rf /Users/grant/repos/mapzen/metroextractor-cities/spec/tmp
mkdir -p /Users/grant/repos/mapzen/metroextractor-cities/spec/tmp
cp -r Rakefile README.md spec/bbox_spec.rb spec/geojson_spec.rb spec/json_spec.rb spec/ruby_spec.rb spec/whitespace_spec.rb tasks/build_geojson.rb tasks/default.rb tasks/test.rb /Users/grant/repos/mapzen/metroextractor-cities/spec/tmp
Running rubocop
rubocop /Users/grant/repos/mapzen/metroextractor-cities/spec/tmp
Inspecting 9 files
.........

9 files inspected, no offenses detected
Validating cities.json bbox's
OK
Validating cities.json syntax
OK
Checking cities.json for invalid whitespace
OK
Validating cities.geojson syntax
OK
```

License and Authors
-------------------
* license: GPL
* authors: grant@mapzen.com
