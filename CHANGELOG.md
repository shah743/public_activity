# Changelog

## 1.6.3

- **Fixed** a bug which resulted in crashes when PostgreSQL connection failed (see #328, thanks to [Ken Greeff](https://github.com/kengreeff))
- **Fixed** a bug which resulted in crashes when MySQL connection failed (see #327, thanks to [Miquel Sabaté Solà](https://github.com/mssola))

## 1.6.2

- **Fixed** a bug which resulted in crashes when database didn't exist (see #323, thanks to [Anmol Chopra](https://github.com/chopraanmol1))

## 1.6.1

- **Fixed** a bug with requiring not existent file in generated migrations

## 1.6.0

* **Add support for Rails 5.2**
* Make config settings thread safe (fixes #284)
* Fix Rspec tests failing in Rails 5 due to ViewHelpers (see #271, thanks to [Janusz](https://github.com/januszm))
* Support JSON, JSONB and HSTORE types for `parameters` column (see #285, thanks to [djvs](https://github.com/djvs) and #315 (thanks to [mateusg](https://github.com/mateusg))

## 1.5.0

* Refactor PublicActivity::StoreController to rely on Thread.current instead. (see #252, thanks to [Ryan McGeary](https://github.com/rmm5t))
* Remove support for Ruby 1.9.3 and Ruby 2.0.0 (thanks to [Ryan McGeary](https://github.com/rmm5t))

## 1.4.2

* Fix bug with migrations not having an extension in ActiveRecord >= 4.0.0

## 1.4.1

* Fixed issue with Rails 4 when using ProtectedAttributes gem (see #128)
* General code clean-ups.

## 1.4.0

* Added support for MongoMapper ORM (thanks to [Julio Olivera](https://github.com/julioolvr)) [PR](https://github.com/pokonski/public_activity/pull/101)
* Added support for stable **Rails 4.0** while keeping compatibility with Rails 3.X
* `render_activity` can now render collections of activities instead of just a single one. Also aliased as `render_activities`
* Fix issue in rendering multiple activities when options were incomplete for every subsequent activity after the first one
* `render_activity` now accetps `:locals` option. Works the same way as `:locals` for Rails `render` method.

## 1.1.0

* Fixed an issue when AR was loading despite choosing Mongoid in multi-ORM Rails applications (thanks to [Robert Ulejczyk](https://github.com/robuye))

## 1.0.3

* Fixed a bug which modified globals (thanks to [Weera Wu](https://github.com/wulab))

## 1.0.2

* Fixed undefined constant PublicActivity::Activity for Activist associations (thanks to [Стас Сушков](https://github.com/stas))

## 1.0.1

* #create_activity now correctly returns activity object.
* Fixed :owner not being set correctly when passed to #create_activity (thanks to [Drew Miller](https://github.com/mewdriller))

## 1.0 (released 10/02/2013)

* **Now supports Mongoid 3 and Active Record.**
* Added indexes for polymorphic column pairs to speed up queries in ActiveRecord
* `#create_activity` now returns the newly created Activity object
* Support for custom Activity attributes. Now if you need a custom relation for Activities you can
  create a migration which adds the desired column, whitelist the attribute, and then you can simply pass the value to #create_activity
* `#tracked` can now accept a single Symbol for its `:only` and `:except` options.
* It is now possible to include `PublicActivity::Common` in your models if you just want to use `#create_activity` method
  and skip the default CRUD tracking.
* `#render_activity` now accepts Symbols or Strings for :layout parameter.
  ### Example

  ```ruby
  # All look for app/views/layouts/_activity.erb
  render_activity @activity, :layout => "activity"
  render_activity @activity, :layout => "layouts/activity"
  render_activity @activity, :layout => :activity
  ```
## 0.5.4

* Fixed support for namespaced classes when transforming into view path.

  For example `MyNamespace::CamelCase` now correctly transforms to key: `my_namespace_camel_case.create`
