<h2>
	For the latest Angular, added customize paginator directive, use for the latest angular2 or above versions
</h2>

Angular service for simple data table with mat-paginator. 

And add table service.
<a href="https://github.com/lmnguyenbt/table-service-for-ngb-paging"> Table Service </a>

First you need to create html:
```html
<mat-paginator style-paginator showFirstLastButtons
               [showTotalPages]="tableService.maxSize"
               [length]="tableService.pagination.total_record"
               [pageSize]="tableService.pagination.length"
               [pageSizeOptions]="tableService.itemPerPageOptions">
</mat-paginator>

```ts
constructor(public tableService: TableService, private httpService: HttpService) {
        this.tableService.context = this;
        this.tableService.searchForm = this.searchForm;
        this.tableService.getFuncName = 'getList';
}

getList() {
    const params = this.tableService.getFilter();

    Object.keys(params).forEach((key) => {
        (params[key] === null || params[key] === '') && delete params[key];
    });

    this.httpService.get[Name]List(params).subscribe((res) => {
        try {
            this.tableService.matchPagingOption(res);
        } catch ( e ) {
            console.log(e);
        }
    });
}

