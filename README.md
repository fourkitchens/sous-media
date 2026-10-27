# Sous Media Drupal Recipe

A recipe that contains modules and configuration for the Sous media experience.

This recipe configures three media types:

- file
- image
- video

## Supported baseline and dependencies

Use the supported Minimal baseline in the [platform guide](https://github.com/fourkitchens/sous-drupal-project/blob/main/docs/PLATFORM.md),
with its Composer dependencies installed. Sous Media does not require Sous Admin. It declares
and enables Field Group and Scheduler itself. Scheduler publication fields stay
hidden in the three media forms, keeping their configuration consistent when composing recipes
with Sous Admin or Sous Content Types.

Reusable media bundles, fields, widgets, and formatters belong to this recipe.
Core-provided `media.full` and `media.media_library` view modes are imported from
Media/Media Library rather than copied into this repository. They were verified
byte-identical against the selected Drupal 11.4.11 defaults before removal;
existing matching configuration is accepted as before. Generated sites own
their complete exports, including those core modes and any project overrides.
Updating this recipe package does not update already-applied configuration;
review package/database updates and explicit site migrations separately.

## Installing this Recipe

These examples select the current unreleased implementation on `dev-main`.
Run them in a configured consuming site, not in this recipe source checkout.
[Setup and recipe prerequisites](https://github.com/fourkitchens/sous-drupal-project/blob/main/docs/SETUP.md) define the required
repositories, installer paths, core unpacking plugin, and explicit root stability
exceptions. Use reviewed stable tags once the coordinated releases exist.

`ddev composer require fourkitchens/sous-media:dev-main`

## Applying this Recipe

If you used the Sous Project as your starterkit:

- `ddev install-recipe fourkitchens/sous-media`

Without the Sous DDEV command, use a configured consuming project and run from its root:

- `ddev drush recipe /var/www/html/web/recipes/sous-media`
- `ddev drush cache:rebuild`

Use the [current native unpacking workflow](https://github.com/fourkitchens/sous-drupal-project/blob/main/docs/SETUP.md) before application.

## Development, integration, and releases

This repository is reusable recipe source, not a generated Drupal application.
Its Composer requirements and `recipe.yml` describe installation defaults; the
consuming project owns its runtime, complete configuration export, custom
theme, and application deployment. Requiring `dev-main` downloads remote source;
it does not test uncommitted sibling checkout changes.

Use the shared documentation instead of maintaining another setup procedure:

- [Supported runtime and package relationships](https://github.com/fourkitchens/sous-drupal-project/blob/main/docs/PLATFORM.md)
- [Fresh installation, contributor clones, restoration, and recovery](https://github.com/fourkitchens/sous-drupal-project/blob/main/docs/SETUP.md)
- [Sibling-source development and integration checks](https://github.com/fourkitchens/sous-drupal-project/blob/main/docs/INTEGRATION.md)
- [Configuration ownership and existing-site upgrades](https://github.com/fourkitchens/sous-drupal-project/blob/main/docs/MAINTENANCE.md)
- [Frontend development and production assets](https://github.com/fourkitchens/sous-drupal-project/blob/main/docs/BUILD_TOOLS.md)
- [Production deployment](https://github.com/fourkitchens/sous-drupal-project/blob/main/docs/DEPLOYMENT.md)
- [Coordinated releases and Conventional Commits](https://github.com/fourkitchens/sous-drupal-project/blob/main/docs/RELEASES.md)
- [Maintenance ownership and review cadence](https://github.com/fourkitchens/sous-drupal-project/blob/main/docs/OPERATIONS.md)

Recipe release tooling runs with the Node/npm versions pinned in `.nvmrc` and
`package.json`; Node is not required to execute a recipe in Drupal. The private
npm package publishes no browser assets or npm release. The thin workflow calls
the shared integration gate before the guarded GitHub publisher. Its central
workflow must be rolled out first; source configuration is not proof of a live
GitHub run or release. See the release guide for actual tag state, stable-tag
adoption, and explicit development exceptions.

Package updates do not automatically change configuration already applied to a
site. Preserve its complete export and adopt changes through reviewed native
configuration migrations and project-owned overrides. Do not routinely replay
the entire recipe on a customized site.

## License

Sous recipe source is licensed under [GPL-2.0-or-later](LICENSE). Dependencies
retain their own license terms; see the shared license policy in the platform
guide.
