
# Q1. Explain what the simple `List` component does.
Ans.- In React js multiple items can be declare as collection using component. This ui components are known as List component. This component can takes an array of items as a prop and maps over this array to create a list of items. Each item in the array is rendered as a list item using the "li" tag in HTML.


#  What problems / warnings are there with code?
1. In WrappedSingleListItem onClickHandler prop expects an argument to be passed to it when it is called so need to wrap it is arrow function.
2. Under WrappedListComponent selectedIndex should be the variable and setSelectedIndex should be the function for useState hook.
3. Inside return of WrappedListComponent key is not assign for items.map.
4. Syntax Error in WrappedListComponent.propTypes. Protypes.array,proptypes.shapeof.
5. WrappedListComponent defaultProps can not be null as mamping can't be done in null.




