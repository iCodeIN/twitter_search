# twitter_search
Work in progress...
```js
var key_word = 'from:'
var new_element_based_on_suggestion_box = `
<div class="css-1dbjc4n r-4amgru r-1p6iasa">
<div class="css-1dbjc4n r-14lw9ot r-1ets6dv r-sdzlij r-1phboty r-rs99b7 r-18u37iz r-ero68b r-1udh08x r-1udbk01" style="height:100%">
<div aria-label="Follow Space missions Topic" role="button" tabindex="0" class="css-18t94o4 css-1dbjc4n r-1awozwy r-18u37iz r-16y2uox r-1wbh5a2 r-1ny4l3l r-ymttw5 r-j2kj52 r-o7ynqc r-6416eg">
<div dir="auto" class="css-901oao css-1hf3ou5 r-18jsvk2 r-1qd0xha r-a023e6 r-b88u0q r-rjixqe r-bcqeeo r-lrvibr r-13qz1uu r-qvutc0">
<span class="css-901oao css-16my406 r-poiln3 r-bcqeeo r-qvutc0">${key_word}</span>
</div>
</div>
</div>
</div>
`
function get_reactfiber(element) {
 var key = Object.keys(element).find(key=>key.startsWith("__reactFiber$"))
 return element[key]
}
const react_element = $('form[aria-label="Search Twitter"]').parentElement.parentElement.parentElement
for (react_element.querySelectorAll('[role="option"]')[14]
const search_label = react_element.querySelector('label') //$('[data-testid="SearchBox_Search_Input_label"]')
search_label.querySelector('input').oninput = function (event) {
  var element = event.target
  event.preventDefault()
  var regex = new RegExp(`^${key_word}\$`,'i')
  if (regex.test(element.value)) {
    var react_element_reactfiber = get_reactfiber(react_element)
    react_element_reactfiber.child.stateNode.shouldComponentUpdate = function (nextProps,nextState) {
      nextProps.filter = ["userS"] // "S" is not a typo
      return true
    }
    react_element_reactfiber.child.stateNode.setQuery('@')
    search_label.firstChild.insertAdjacentHTML('afterend',new_element_based_on_suggestion_box)
  }
}
```
