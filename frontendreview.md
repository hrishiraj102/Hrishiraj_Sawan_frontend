
# Q1. Explain what the simple `List` component does.
Ans.- In React js multiple items can be declare as collection using component. This ui components are known as List component. This component can takes an array of items as a prop and maps over this array to create a list of items. Each item in the array is rendered as a list item using the "li" tag in HTML.


#  What problems / warnings are there with code?
1. In WrappedSingleListItem onClickHandler prop expects an argument to be passed to it when it is called so need to wrap it is arrow function.
2. Under WrappedListComponent selectedIndex should be the variable and setSelectedIndex should be the function for useState hook.
3. Inside return of WrappedListComponent key is not assign for items.map.
4. Syntax Error in WrappedListComponent.propTypes. Protypes.array,proptypes.shapeof.
5. WrappedListComponent defaultProps can not be null as mamping can't be done in null.


# Ans3 Code Fix
import React, { useState, useEffect, memo } from 'react';
import PropTypes from 'prop-types';

// Single List Item
const WrappedSingleListItem = ({
    index,
    isSelected,
    onClickHandler,
    text,
}) => {
    return (
        <li
            style={{ backgroundColor: isSelected ? 'green' : 'red' }}

            onClick={() => onClickHandler(index)} //including index using function
        >
            {text}
        </li>
    );
};


WrappedSingleListItem.propTypes = {
    index: PropTypes.number.isRequired,
    isSelected: PropTypes.bool.isRequired,
    onClickHandler: PropTypes.func.isRequired,
    text: PropTypes.string.isRequired,
};


const SingleListItem = memo(WrappedSingleListItem);

// List Component
const WrappedListComponent = ({
    items,
}) => {
    const [selectedIndex, setSelectedIndex] = useState(); //null is false and will define !isSelected

    useEffect(() => {
        setSelectedIndex(null);
    }, [items]);

    const handleClick = index => {
        setSelectedIndex(index);
    };

    return (
        <ul style={{ textAlign: 'left' }}>
            {items.map((item, index) => (
                <SingleListItem key={index} // Key is very important for List for identification of which item
                    onClickHandler={() => handleClick(index)}
                    text={item.text}
                    index={index}
                    isSelected={selectedIndex === index}   // isSelected is boolean proptypes and selectIndex is number(index) so converting to bool
                />
            ))}
        </ul>
    )
};

WrappedListComponent.propTypes = {
    items: PropTypes.arrayOf(PropTypes.shape({
        text: PropTypes.string.isRequired,
    })),
};

WrappedListComponent.defaultProps = {
    items: [] //Null cannot be map so default much contain object
};

const List = memo(WrappedListComponent);

export default List;

