# jQuery Pagination Plugin 

This is my second plugin made as jQuery course final project :mortar_board: - slightly adopted from my Smart Table project. 
The Pagination Plugin is aimed to divide selected html elements into pages which number is specified by user in the option parameters.
As an example of paginated elements are images with my poems.  

![alt tag](images/Pagination_example) 

## Descritpion and application 

The pagination plugin is available in :open_file_folder: js/jquery_plugin_pagination.js and can be viewed in browser by index_jquery.html.
Plugin structure follows jQuery Lightweight pattern. 

## Example of usage and input options

To bring pagination to life you need to: 

:pushpin: Choose and element from your HTML code that will contain elements for pagination: 

``` 
var $element = $('table');
``` 

:pushpin: Define options with number of elements per page and the element type to be selected to the list: 

``` 
 var options1 = {
    rowsPerPage: 2,
    elementToSelect: 'tr'
 };
``` 

:pushpin: As a last step make your dream come true and evoke pagination of the chosen elements:

``` 
$element.pagination($element, options1);

``` 

## Plugin methods example 

And here is a piece of my code style with comments (onClickShowNextPageHandler @private method):

``` 
 /**
 * Displays the next page rows in relation the currently chosen ones
         * @param {object} event 
         * @callback
         * @private
         */
        Plugin.prototype.onClickShowNextPageHandler = function (event) {
            /**
             * Represents a button which coressponding rows are currently displayed
             * It is selected thanks to the style attribute related to highliting 
             * @type {nodeElement} */
            var $currentPageButton = $(this.element).find('button[style]');
            var $nextPageButton = $currentPageButton.next();
            this.paginationInitialConditions(); 
            var text = $currentPageButton.text();  
            var pageNo = parseInt(text,10);
            var currentPageNumber = pageNo +1;
            // Pamietaj, pageNo ma nr wiekszy niz indeks w pagesArray!
            if (pageNo === this.pagesArray.length) {
                $(this.pagesArray[pageNo-1]).each(function (index, element) {
                    $(element).css('display', '');
                }); 
                this.chosenButtonHighlight($currentPageButton);
            } else {
                $(this.pagesArray[pageNo]).each(function (index, element) {
                    $(element).css('display', '');
                });
                this.chosenButtonHighlight($nextPageButton);
            };
        };
``` 

## Further Documentation 

:closed_book: I prepared a detailed documentation using jsdoc. It is available in :open_file_folder: /js/out/index.html 

## How can I support developers? 

:+1: Support me with stars, good advice and keep your fingers crossed for my future in IT :smiley: 

## Features 
 
* Pagination (run externally) 

## License 

[MIT](LICENSE.txt) license

## Special thanks 

Special thanks to Adrian, my teacher, to teach me extra JEDI(LE) JS force :smiley: