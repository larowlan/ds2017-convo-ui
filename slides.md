## Using aggregate queries to boost performance

--

## Scenario

- you need to access field values
- for a lot of entities
- you don't need all fields

--

## Typical approach

<pre><code>
$storage = \Drupal::service('entity_type.manager')->getStorage($node);
$some_field_values = [];
foreach ($storage->loadMultiple($heaps_of_ids) as $node) {
  $some_field_values[$node->id()] = $node->some_field->value;
}
</code></pre>

--

## Ok, so that works?

- Right but it loads all of the field values
- And if you've got a lot of fields
- Or a lot of nodes

--

## And what about revisions 
Whilst we have
<pre>
<code>
$storage->loadMultiple($stacks_of_ids);
</code></pre>
We don't have
<pre>
<code>
$storage->loadMultipleRevisions($stacks_of_revision_ids);
</code></pre>

--

## Enter aggregate queries

--

## What is an aggregate query?

- its kind of like entity query
- but you can get field values
- and revisions 
- without loading full entities

--

## Aggregate query in action

Getting field values
<pre>
<code>
$query = $storage->getAggregateQuery();
// Normal Entity query stuff.
$results = $query->condition('type', 'article')
  // Aggregate stuff
  ->groupBy('field_some_field.target_id')
  ->groupBy('nid')
  ->execute();
$some_field_values = array_combine(
  array_column($results, 'nid'),
  array_column($results, 'field_some_field_target_id')
);
</code>
</pre>

--

## Revisions

Revision values

<pre>
<code>
$query = $storage->getAggregateQuery()
  // All revisions.
  ->allRevisions();
// Normal Entity query stuff.
$results = $query->condition('type', 'article')
  // Aggregate stuff
  ->groupBy('field_some_field.target_id')
  ->groupBy('vid')
  ->execute();
$some_field_values = array_combine(
  array_column($results, 'vid'),
  array_column($results, 'field_some_field_target_id')
);
</code>
</pre>

--

## Questions?
