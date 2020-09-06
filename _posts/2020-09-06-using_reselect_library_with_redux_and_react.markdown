---
layout: post
title:      "Using Reselect Library with Redux and React"
date:       2020-09-06 07:46:55 +0000
permalink:  using_reselect_library_with_redux_and_react
---


What is Reselect?

Reselect is a simple selector library aimed at reducing the amount of unnecessary calculations that occur after Redux state changes. Reselect does this by giving developers the ability to create memoized selectors - using createSelector - that will only update when changes occur to state that directly affects the selector. As an application’s state grows these savings can really improve the overall performance of the application.

Installing Reselect 

Reselect is easily added to any project with … ‘npm install reselect’ if using npm or ‘yarn add reselect’ if using yarn. 

Using Reselect

In order to keep the application organized it is a good practice to define selectors in their own JS file and then importing them wherever they are needed. For example, in the online store application I am working on the state was made up of multiple sections (user, cart, shop) and each section had its own selector file. The createSelector function can then be imported from the reselect library with … 

Import { createSelector } from ‘reselect’

The createSelector function takes in two arguments, the first is a collection of input selectors and the second is a function that will return the desired value from the selector. Here is an example …

const selectCart = state => state.cart

export const selectCartItems = createSelector(
	[selectCart],
	cart => cart.cartItems
)

export const selectCartTotal = createSelector(
	[selectCartItems],
	cartItems => cartItems.reduce(
		(accumulatedQuantity, cartItem) => 
		accumulatedQuantity + (cartItem.quantity * cartItem.price),
		0
	}
)

These functions can then be imported into other files and are typically added to mapStateToProps. Here is an example:

const mapStateToProps = createStructuredSelector({
	cartItems: selectCartItems,
	Total: selectCartTotal
})


CreateStructuredSelector just allows the combination of multiple selectors into a single object. The keys of these objects can then be accessed in the props of the component. And that is all there really is to it. 

Conclusion

Memoized selectors help make state changes more efficient by reducing the amount of state that actually gets rerendered. Using a library like Reselect makes adding these selectors extremely easy for developers and can offer a nice performance boost to the application, especially as state grows more complex. I personally really like using selectors and plan on using them for all projects in the future.



The content of your blog post goes here.
