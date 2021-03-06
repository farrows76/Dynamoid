# HEAD

# 1.3.3

* Allow configuration of the Dynamoid models directory, as not everyone keeps non AR models in app/models
  - Dynamoid::Config.models_dir = "app/whatever"

# 1.3.2

* Fix migrations by stopping the loading of all rails models outside the rails env.

# 1.3.1

* Implements #135
  * dump values for :integer, :string, :boolean fields passed to where query
    * e.g. You can search for booleans with any of: `[true, false, "t", "f", "true", "false"]`
* Adds support for Rails 5 without warnings.
* Adds rake tasks for working with a DynamoDB database:
  * rake dynamoid:create_tables
  * rake dynamoid:ping
* Automatically requires the Railtie when in Rails (which loads the rake tasks)
* Prevent duplicate entries in Dynamoid.included_models
* Added wwtd and appraisal to spec suite for easier verification of the compatibility matrix
* Support is now officially Ruby 2.0+, (including JRuby 9000) and Rails 4.0+

# 1.3.0

* Fixed specs (@AlexNisnevich & @pboling)
* Fix `blank?` and `present?` behavior for single associations (#110, @AlexNisnevich & @bayesimpact)
* Support BatchGet for more than 100 items (#80, @getninjas)
* Add ability to specify connection settings specific to Dynamoid (#116, @NielsKSchjoedt)
* Adds Support for Rails 5! (#109, @gastzars)
* Table Namespace Fix (#79, @alexperto)
* Improve Testing Docs (#103, @tadast)
* Query All Items by Looping (#102, @richardhsu)
* Store document in DocumentNotValid error for easier debugging (#98, holyketzer)
* Better support for raw datatype (#104, @OpenGov)
* Fix associative tables with non-id primary keys (#86, @everett-wetchler)

# 1.2.1

* Remove accidental Gemfile.lock; fix .gitignore (#95, @pboling)
* Allow options to put_items (#95, @alexperto)
* Support range key in secondary index queries (#95, @pboling)
* Better handling of options generally (#95, @pboling)
* Support for batch_delete_item API (#95, @pboling)
* Support for batch_write_item API (#95, @alexperto)

# 1.2.0

* Add create_table_syncronously, and sync: option to regular create_table (@pboling)
  * make required for tables created with secondary indexes
* Expose and fix truncate method on adapter (#52, @pcorpet)
* Enable saving without updating timestamps (#58, @cignoir)
* Fix projected attributes by checking for :include (#56, @yoshida_tetsuhiro)
* Make behavior of association where method closer to AR by cloning instead of modifying (#51, @pcorpet)
* Add boolean field presence validator (#50, @pcorpet)
* Add association build method (#49, @pcorpet)
* Fix association create method (#47, #48, @pcorpet)
* Support range_between (#42, @ayemos)
* Fix problems with range query (#42, @ayemos)
* Don't prefix table names when namespace is nil (#40, @brenden)
* Added basic secondary index support (#34, @sumocoder)
* Fix query attribute behavior for booleans (#35, @amirmanji)
* Ignore unknown fields on model initialize (PR #33, @sumocoder)

# 1.1.0

* Added support for optimistic locking on delete (PR #29, @sumocoder)
* upgrade concurrent-ruby requirement to 1.0 (PR #31, @keithmgould)

# 1.0.0

* Add support for AWS SDK v2.
* Add support for custom class type for fields.
* Remove partitioning support.
* Remove support for Dynamoid's (pseudo)indexes, now that DynamoDB offers
  local and global indexes.
* Rename :float field type to :number.
* Rename Chain#limit to Chain#record_limit.

Housekeeping:

* Switch from `fake_dynamo` for unit tests to DynamoDBLocal. This is the new authoritative
  implementation of DynamoDB for testing, and it supports AWS SDK v2.
* Use Travis CI to auto-run unit tests on multiple Rubies.
* Randomize spec order.
