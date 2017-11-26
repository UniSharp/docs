<!-- TITLE: Laravel Custom Paginator -->
<!-- SUBTITLE: A quick summary of Laravel Custom Paginator -->

# Custom Paginator

## LengthAwarePaginator

```
void __construct( 
    mixed $items,
    int $total,
    int $perPage,
    int|null $currentPage = null, 
    array $options = array()
)
```



In Controller

```
$perPage = 15;
$pageStart = \Request::get('page', 1);
$offSet = ($pageStart * $perPage) - $perPage;
// paginator 只負責渲染出分頁的 html 以及頁數的邏輯，但是並不負責把資料切段
// 因此應放 take()->skip() 過的資料進去 paginator
$itemsForCurrentPage = array_slice($user->refundLogs(), $offSet, $perPage, true);

$paginator = new LengthAwarePaginator(
    $itemsForCurrentPage,
    count($user->refundLogs()),
    $perPage,
    Paginator::resolveCurrentPage(),
    array('path' => Paginator::resolveCurrentPath())
);
```

In Pugs

```
table.table.table-striped.table-bordered.table-middle
    thead
      th 
    tbody
      | @foreach($paginator as $entity)
      td
      ...
      | @endforeach
| {!! $paginator->render(); !!}
```

Appending to pagination links

```
{!! $paginator->appends(['parent_id' => '1'])->render() !!}
// {url}?parent_id=1
```



