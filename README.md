# jsdragtable
A simple JQuery extension for enabling draggable columns on tables. This works on standard HTML tables with <thead> and <tbody> sections defined including support for touch-enabled devices.

###Simple Usage

```
$({selector}).jsdragtable();
```

An example is shown on [jsfiddle](http://jsfiddle.net/brentj73/hs2n71mo/).

**14.11.2015

-options added

####options:

 `skipFirst` - Prevent dragging first column. Default `true`   
 
 `handleElementName` - If specified check event . Default `true`  
  
 `dropEvent` - Function to process drop event. Useful for save sort order.



#### example with options

```
$({selector}).jsdragtable({
    skipFirst: false,
    handleElementName: 'th',
    dropEvent: function(container){
      var sort = [];
      $(container).find("th").each(function (headerIndex, header) {
                        sort[headerIndex] = $(header).data('class-pk');
                    });
                    if(sort.length){
                        var tableId = $('#tableId').val();
                        var data = {sort: sort};
                        $.ajax({
                            type: 'POST',
                            url: '/table/' + tableId + '/sort',
                            data: data
                        });
                    }
    }    
});
```
