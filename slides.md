<!-- .slide: data-background="./images/blueprint.jpg" -->

## A blueprint for a secure<br>Drupal 8 platform<br>and build process<br>with composer

Note:

-

--

<!-- .slide: data-background="./images/boxing.jpg" -->

## Let's get it out there

--

<!-- .slide: data-background="./images/musicians.jpg" -->

## If you're not using composer with Drupal 8

--

<!-- .slide: data-background="./images/wrong.jpg" -->

## You're doing it wrong

--

<!-- .slide: data-background="./images/bundy.jpg" -->
## Who am I?

@larowlan

Note:

- by way of introduction
- 8 years of Drupal
- 450+ core patches
- Maintain 4 core modules
- 40+ contrib modules
- security team member
- senior drupal dev at @pnx

--

<!-- .slide: data-background="./images/package.jpg" -->

## Composer basics

Note: 

- Composer is a package manager for PHP
- Think bundler/gem for Ruby or npm for JavaScript/Node

--

<!-- .slide: data-background="./images/bp-1.jpg" -->

## composer.json

Note:

- Nominate required packages and version constraint
- Nominate autoloading (see my other session)
- Dev dependencies (e.g. testing framework)
- Directories to place stuff in

--

<!-- .slide: data-background="./images/bp-2.jpg" -->

## composer.lock

Note:

- artefact
- Repeatable builds
- Hash of versions used
- Always commit your lock if you expect repeatable builds

--

<!-- .slide: data-background="./images/bp-3.jpg" -->

## Adding a dependency

- <code>composer require "symfony/yaml:~2.8"</code>

--

## Version constraints

<!-- .slide: data-background="./images/bp-4.jpg" -->

- ~1.2
- ^1.2.0
- dev-{branchname}
- 1.2.3
- dev-{branchname}#{sha}

--

<!-- .slide: data-background="./images/bp-5.jpg" -->

## Installing

- <code>composer install --prefer-dist</code>

--

<!-- .slide: data-background="./images/bp-6.jpg" -->

## Updating

- <code>composer update</code>
- <code>composer update "drupal/core" --with-dependencies</code>
- <code>composer update "drupal/*" --with-dependencies</code>

--

<!-- .slide: data-background="./images/bp-7.jpg" -->

## Outdated

- <code>composer outdated</code>

--

<!-- .slide: data-background="./images/bp-8.jpg" -->

## Drupal 8

- Start with the template
- <code>composer create-project drupal-composer/drupal-project:8.x-dev myproject --stability dev --no-interaction</code>

--

<!-- .slide: data-background="./images/bp-9.jpg" -->

## drupal.org Packagist

- <code>composer config repositories.drupal composer https://packages.drupal.org/8</code>
- <code>composer require "drupal/entity_hierarchy:~2.0"</code>

Note:

- sensible defaults

--

<!-- .slide: data-background="./images/bp-10.jpg" -->

## Plugins

- Many of these included in Drupal project template

--

<!-- .slide: data-background="./images/bp-11.jpg" -->

## Composer installers

- <code>composer require "composer/installers:~1.0"</code>

--

<!-- .slide: data-background="./images/bp-12.jpg" -->

## Composer installers

<pre><code type="text/javascript">
"extra": {
    "installer-paths": {
        "app/core": [
            "drupal/core"
        ],
        "app/modules/contrib/{$name}": [
            "type:drupal-module"
        ],
        "app/themes/contrib/{$name}": [
            "type:drupal-theme"
        ],
    },
    "enable-patching": true
}
</code></pre>

--

<!-- .slide: data-background="./images/bp-13.jpg" -->

## Composer patches

- <code>composer require "cweagans/composer-patches:~1.5"</code>

--

<!-- .slide: data-background="./images/bp-1.jpg" -->

## Composer patches

<pre><code type="text/javascript">
"extra": {
    "patches": {
        "drupal/core": {
            "Allow BTB to run against existing site": "https://www.drupal.org/files/issues/2793445-25-8.2.x.patch",
         }
     }
}
</code></pre>

--

<!-- .slide: data-background="./images/bp-2.jpg" -->

## So what does this have to do with security?

--

<!-- .slide: data-background="./images/bp-3.jpg" -->

## Let's talk about audits

Note:

- One of the services we provide at PNX is auditing of projects
- One element of that is security
- PNX are the only Australian team with staff on the Security Team
- We have two, Ben Dougherty and myself

--

<!-- .slide: data-background="./images/bp-4.jpg" -->

## Steps in the audit process

- Determine if the site is running insecure versions

Note:

- drush upc --security-only

--

<!-- .slide: data-background="./images/bp-5.jpg" -->

## Steps in the audit process

- Determine if any contrib or core code has been modified

Note:

- Now we have third party code, this increases tenfold
- 68M of code in app/core
- 58M in vendor

--

<!-- .slide: data-background="./images/bp-6.jpg" -->

## The audit surface is huge

- although hacked.module can help

Note:

- if you've checked in core 68M of code
- if you've checked in vendor 58M of code
- plus contrib code probably of the order of 20 - 30M of code

--

<!-- .slide: data-background="./images/bp-7.jpg" -->

## Everytime you hack core

- a kitten gets it

Note:

- when we audit, we look for patches
- core has bugs (thousands of them)
- patching is a reality
- patching is fine
- hacking without patches is not fine

--

<!-- .slide: data-background="./images/bp-8.jpg" -->

## No patches?

- good luck with that critical security update

Note:

- Patch files let you update smoothly
- No snowflakes
- Patches from d.o get re-rolled
- You're not alone

--

<!-- .slide: data-background="./images/bp-9.jpg" -->

## So what is left?

Note:

- Take out core
- Take out contrib
- Take out vendor

--

<!-- .slide: data-background="./images/bp-10.jpg" -->

## Custom code

- Themes
- Modules

--

<!-- .slide: data-background="./images/bp-11.jpg" -->

## That's it

- Congratulations, you know have a much smaller audit surface

--

<!-- .slide: data-background="./images/bp-12.jpg" -->

## New audit process

- Check for insecure core/module versions

Note:

- drush upc --security-only --dry-run

--

<!-- .slide: data-background="./images/bp-13.jpg" -->

## Any alphas or dev versions?

- Check composer.json
<pre><code>composer show --installed</code></pre>

Note:

- stable modules are covered by security team
- no audits, but security vulnerabilities handled in private
- if you use a dev/alpha/beta version, check the maintainer reputation
- follow the issue queue to be across security/major issues

--

<!-- .slide: data-background="./images/bp-1.jpg" -->

## <del>Stable = security team coverage</del>

March 2013: Not all stable modules are created equal

https://github.com/larowlan/composer_drupal_security
https://www.drupal.org/node/2863103

Note:

- working to get coverage flag in composer.json extra
- https://github.com/larowlan/composer_drupal_security

--

<!-- .slide: data-background="./images/bp-2.jpg" -->

## Vetted module lists?

- Instead minimum-stability flags?
<pre><code type="text/javascript">"minimum-stability": "stable"
</code></pre>

Note:
- Composer supports minimum stability flags
- dev/alpha/beta/RC/stable

--

<!-- .slide: data-background="./images/bp-3.jpg" -->

## Out of date third party code?

- <pre><code>composer outdated</code></pre>
- Not limited to security
- Includes unsupported

--

<!-- .slide: data-background="./images/bp-4.jpg" -->

## Third-party security<br>vulnerabilities

- Sensiolabs security database & checker

--

<!-- .slide: data-background="./images/bp-5.jpg" -->

## Web version

- https://security.sensiolabs.org
- Upload your composer.lock

Note:

- remember I said always check in the lock file
- this is why
- its your guarantee

--

<!-- .slide: data-background="./images/bp-6.jpg" -->

## Tooling

<code>composer require sensiolabs/security-checker --dev</code>


<code>./bin/security-checker security:check ./composer.lock</code>

Note:

- automate into your build process
- fail insecure builds/deploys
- you have a build right? if not we consult on that stuff

--

<!-- .slide: data-background="./images/bp-7.jpg" -->

## How does it work?

- https://github.com/FriendsOfPHP/security-advisories

Note:

- open source database of PHP project CVEs (common vulnerabilities and exposures)

--

<!-- .slide: data-background="./images/bp-8.jpg" -->

## Does it include Drupal?

- For core, yes
- For contrib, not yet (we're working on it)

Note:

- We need d.o to make security advisories available as their own node-type instead of a forum post, so we can automate
- We need the security checker to support packagist repos outside packagist (drupal.org)

--

<!-- .slide: data-background="./images/bp-9.jpg" -->

## Something more formal

- PSR-9 and PSR-10

Note:

- Not all PHP projects are created equal
- e.g. Drupal has security team and private process
- Symfony has private per issue invite only repos/teams
- No common/formalised reporting process
- No common disclosure process

--

<!-- .slide: data-background="./images/bp-10.jpg" -->

## Questions?

- https://www.drupal.org/docs/develop/using-composer/using-composer-to-manage-drupal-site-dependencies
- ping me on irc in #drupal-au to discuss more

--

<!-- .slide: data-background="./images/bp-11.jpg" -->

## Image credits

<ul class="tight">
<li>https://www.flickr.com/photos/statelibraryqueensland/25487330522</li>
<li>https://www.flickr.com/photos/statelibraryqueensland/25487330522</li>
<li>https://www.flickr.com/photos/statelibraryqueensland/16618698644</li>
<li>https://www.flickr.com/photos/statelibraryqueensland/4312619111</li>
<li>https://www.flickr.com/photos/statelibraryqueensland/4461115473</li>
<li>https://www.flickr.com/photos/statelibraryqueensland/4189609872</li><li>
https://www.flickr.com/photos/statelibraryqueensland/25478967541</li><li>
https://www.flickr.com/photos/statelibraryqueensland/25276069800</li><li>
https://www.flickr.com/photos/statelibraryqueensland/25478962321</li><li>
https://www.flickr.com/photos/statelibraryqueensland/25276070990</li><li>
https://www.flickr.com/photos/statelibraryqueensland/25204135719</li><li>
https://www.flickr.com/photos/statelibraryqueensland/25453113632</li><li>
https://www.flickr.com/photos/statelibraryqueensland/24941183594</li><li>
https://www.flickr.com/photos/statelibraryqueensland/25514085021</li><li>
https://www.flickr.com/photos/statelibraryqueensland/25606753555</li><li>
https://www.flickr.com/photos/statelibraryqueensland/24980052313</li><li>
https://www.flickr.com/photos/statelibraryqueensland/25571686705</li><li>
https://www.flickr.com/photos/statelibraryqueensland/24941185404</li><li>
https://www.flickr.com/photos/statelibraryqueensland/24944998423</li>
</ul>
