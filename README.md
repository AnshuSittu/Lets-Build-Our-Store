# Lets-Build-Our-Store
Namste React Episode 12


#Redux-ToolKit
  -Install @reduxjs/toolkit and react-redux two lib
  -Build our store
  -connect our store to our application
  -Create slice(cartSlice)
  -Dispatch an action 
  -READ DATA using SELECTOR


How to create REDUX STORE
How to mange state using REDUX
How to Data state using REDUX

>REDUX is not mandatory this in small scale application 
>it is for the large scale application where the data is heavily used where a lot of 
 read and write operation is happing on UI Application
> <b>REDUX and React are different Libraries </b>
>REDUX is a Separate Libraries which we import/Install in our Project and then  we use  REDUX Capabilities 
>REDUX is not the only Libraries that is used for managing state 
>zustand is another very popular Libraries 

Why DO WE USED REDUX
>when we are building Large Scale Application REDUX Offers you great solution for it 
 HANDLING DATA  MANAGING DATA HANDLING YOUR STORE 
> REDUX is primary used for handling state of our application
>when we use REDUX our application become easier to debug

There are two Libraries which REDUX Team offers 
  
  I.  React-Redux
  II. Redux ToolKit
  
>In this we are using Redux ToolKit
 as it is the most recent one and widely used today 

>Redux ToolKit is a newer way of writing redux 
> We will be using React-Redux 

**Why Redux ToolKit RTK **

>The Redux Toolkit package is intended to be the standard way to write Redux logic. 
 It was originally created to help address three common concerns about Redux:

   I.   Configuring a Redux store is too complicated
   II.  We have to add a lot of packages to get Redux to do anything useful
   III. Redux requires too much boilerplate code


What is Redux Store?
> it is nothing a big Object and kept in a global central place
  and we keep all the data in a central place not all the data exactly but most of the major DATA
  of our application into the Redux Store  
> we have part of our REDUX Store called as Slices or slices of Redux Store 
> it is a small proration of REDUX Store 
> we create Multiple slices over REDUX Store  

** Why Do We need Slices and what are these slices actually
> what are the different slices in our food ordering App ??
> to keep data separate we make logical partition and this partition are the slices
> we can create user slice to store user information 
> so whatever you need to create we will create logical separation and make small slices of redux stroe 
>There can be cart,user,them, slice diffrent type of slices 

>>We will be creating card slice which hold all the information of cart 
> initially this cart can be empty array 
>later on we put data inside it can modify the cart slice  i.e data inside cart slice 


**On a click of add button how does the data go on cart slice **
> we can not add data to the cart slices its not simple 
>Redux says that you can not directly modify the cart slices 
> there is a way we can do that  

** Way TO modify the Cart Slices **
> if I click on add button then I will have to dispatch an action
>i.e when you click on Add btn then it dispatches an action
> after dispatch an action what happen it calls a function   
> so now when you click this add button then it dispatch an action and then it calls a function 
  this function modify this cart   
>This function eternally modify the cart  
 
** What is this function actually ** 
> this function is basically know as Reducer Function 
> this Reducer Function  modify our cart 

<b>
Note: when you hit the Add(+) button it dispatch an action which calls the Reducer Function 
      which update the slice of our Redux Store 
	  </b>
> Then Our SLice will be updated 
>This item(item which has been added by clicking the add btn ) will be added to our slice 

>Now cart slice have some data inside it
>this is how to write Data now how to READ data 

** How To READ DATA **
> Now get the data over Cart by showing how many item have been added to cart refer image 0:30:00
> suppose we have added 3 item before now added one more then it should Change to 4 
> So to READ data now we use something know as SELECTOR 
> we will use SELECTOR to read the data from our store and this SELECTOR will modify our react component
> this process is know as the subscribing to the store 
> so if the data in store changes the My header component will update automatically 
> This REDUX will auto magically update the data inside the header as soon as my store changes 
> that is why we called it subscribing to the store 
> basically our header component over here is subscribe to the store here 
> this is done by using SELECTOR


>So first of all when you click on add button it will dispatch an Action
>it will call Reducer Function 
>which updated the slice of our REDUX Store
>and our Cart component is subscribed to the store using SELECTOR 


#Redux-ToolKit
  -Install @reduxjs/toolkit and react-redux two lib
  -Build our store
  -connect our store to our application
  -Create slice(cartSlice)
  -Dispatch an action 
  -READ DATA using SELECTOR

  

** How To build Our Own Store 
> we build Our Own store Inside our utils 
> need to create appStore.js file in utils 
> now we will use a function know as configureStore to create our store 
> configureStore will come from @reduxjs/toolkit
> this configureStore will gives us our store of our react application.
> this how we build our App store 
> we will add slices to this store
> then export default appStore
> we will add slice inside it 
> Now provide this store to our App i.e in root file which is app.js 


How to provide Store to our App
> we need something know as provider which comes from react-redux
>it is imported from react-redux
  import { Provider } from "react-redux";

>  there is difference between two libraries 
>this reduxjs/toolkit or RTK lib has thing to do with redux 
>so creating a store is a redux thing 
>that is why configureStore store comes from redux toolkit
>but now we have to provide this to store to a react app
>So its a kind of bridge in between our react application and redux 
>so that's is why this provider comes from react redux 

>Configuring store is a redux job 
>providing it to react application is react-redux Job 

>Now we will wrap whole our application in that provider just like we use this user context 
 
  <Provider store={}>
    <userContext.Provider value={{ loggedInUser: userName,setUserName}}>
      <div className="app">
        <Header />
        <Outlet />
      </div>
    </userContext.Provider>
    </Provider>

>We will pass this store as props over here 
>This Store key is very Important 
>this Provider has been exported from the react-redux library 
>and what store it will take ?
>it will take <b>appStore</b> and it will imported from our utils / appStore
>SO now this store we have provided to our application
>Now basically we have warped our whole app inside this store 
>SO Now if we dont want to have REDUX to whole App than in that case then you just provide
 your store to that specific portion of the app.
>so whenever you need to use store you have to wrap everything inside this provider

** How To Create Slices 
> you can keep a folder for all the redux slices and store but as if now we are keeping everthing in 
  utils
> you need to create a file ex cartSlice.js 
> this card slice will be created by a function which is know as <b>"createSlice"</b>.
> this createSlice will again come from @reduxjs/toolkit because its something which is related to redux.
> this cartSlice is a function which takes a configuration to create a slice 
> the first thing that we have to give it is the name of slice 
> this configuration will have name we can call it cart
> it will take an initial state  
> this initialState is an Object and Object have item
> initial giving as empty array (this items are cart item )
> and then we will have reducers which is basically an Object
> We will write Reducers function corresponding to those actions 
> We will create actions and reducers over here.
> this object has different types of actions that we can take  
> types of action such as Add item remove item and we can clear the cart as well 
> and we can perform all these action and for each corresponding this we will have 
  reducers function 
> this is basically reducers function with the name addItem but this will map to an action 

** How we will modify the slice of the store 
> SO basically it get access to this state 

   reducers: {
    addItem: (state,action ) => { 
    },
> The initial state is empty array and this gets access to the state and now 
  and this also get access to this action 
> And this is our reducer function  
>it gets two parameters (state, action)  
>Now it modify our state based on action  

Note:
>when we will dispatch i.e click on that button we will add item
>so we will get this payload when we will call this add item
  
  state.items.push(action.payload);
  
  

** How we will modify a state of this **
> we will modify the state based on our action 
     clearCart: (state, action)
>we will do a   state.items.push(action.payload);	
>so whatever we will pass in to this function  

   const cartSlice = createSlice({
  name: "cart",
  initialState: {
    items: [],
  },
  reducers: {
    addItem: (state, action) => {
      state.items.push(action.payload);  // this will add 
    },
    removeItem: (state) => {
      state.items.pop();   // this will delete from top
    },

    clearCart: (state, action) => {
      state.items.length = 0;   // this will make state as empty array 
    },
  },
});

>>What will this cart slice have ??<<
>The first thing is name, name of the cart slice 
>The Second thing is the initial state which is the initial value of that
 portion of that store in the redux store. 
> and then some reducers function which will modify the state
>Now we will export two things from here 
  >we will export our Action
  >We will export our Reducers

>Now we will export default createSlice.reducers
 
   export default cartSlice.reducer;
 
>then we will also export our actions 
>Actions which will export will be add remove clear cart etc 
>action will be export from cartSlice.actions 
   
   export const {addItem, removeItem, clearCart} = cartSlice.action;

Note:
>when we will do create Slices this create slice function which will return an Object 
 in this card slice 
>this cars slice will look something like below  
   
 action:  {
       addItem(state, action ),
	   },
	   reducer{
	   }
>SO card slice will be like big Object which has action reducer so
 we are doing export default card slice.reducer .
>We are taking out individually and exporting it.
 
Summarise:
>First of all we do a createSlice   
>This createSlice will take a config 
>this config will have a name lets call it cart 
>and it will take initial state
>This initial state will be an object has some item
> this item are basically cart Item 
>initially it is empty array
> then we will have reducers
> reducers is basically an Object
> this object has different types of action  
 
   
** How to add this slice to store **
> as store is empty right now and we have to add the slices which has been just created 
> to add you create a reducer 
> so if you want to modify a big store it also has a reducer for itself and that reducer
  combines reducer of there slices 
> So this reducer(used in appStore) is responsible to modify the appStore
> this reducer is basically a combination of different small store 
>For each slice we will have a different reducer

>we will import cartReducer from ./cartSlice
   
   import cartReducer from "./cartSlice";

> and now we will do cart and then will do a cartReducer 
> So basically this reducer is basically our app big reducer
> it consist of small reducer from different slices and each slices will have its own reducers
   
    import { configureStore } from "@reduxjs/toolkit";
    import cartReducer from "./cartSlice";

         const appStore = configureStore({
            reducer: {
                   cart: cartReducer,
              },
          });

              export default appStore;   
	
>if we have multiple slices we have added here 
>if we have user slices then we have added user reducer over here 

          const appStore = configureStore({
            reducer: {
                   cart: cartReducer,
				   user: userReducer 
              },
          });

> this cartReducer comes from our cart slice

** we are mutating our state over here (in cartSlice line no 10)

** How DO we Subscribe to our Store **
> Now we have to Subscribe to our store using SELECTOR
> we will be using SELECTOR for Subscribe
> Lets go to the Header.js 

> we have added some dummy value as inital value in our cart 
>to show live Now we have to use SELECTOR to READ 

> SELECTOR is nothing but a Hooks inside react
> and a hook is a normal JS function at the end of the day 
> we will have a SELECTOR and that is know as useSelector Hook
> which comes from react-redux library

** How DO we use this hook **
> So basically this hook will give access to the store 
> Now we are subscribing to the store using a SELECTOR
> this useSelector gives access to our store but now we will tell them
  what portion of store we need access to 
> so suppose if I need access to my store.cart.items  

   const cartItems = useSelector((store) => store.cart.items);

> So this SELECTOR basically helps us to identify what portion of our store I need to read 
> or need to subscribe to...
> we are just subscribing to the small portion that cart item that how much item it have
> Now this cartItems will get data of this .items 
> Now whenever my item will modify my cart item will modify

**How to Use cartItems **
>We can use cart items now just use cart items over Cart(In header section) and write JSX 
   
   <Link to="/cart" className="px-1 mx-1 font-bold text-xl">
              Cart ({cartItems.length} Items)
            </Link>

> and it will give the length of the cart Items 


** How to add items to the Cart or Dispatch an Action **
> so on click of button (itemList +) I want to dispatch an action
>




Note:
>whenever you are doing a selector male sure you are subscribing to the right portion of the store 

>if you dont subscribe to the right portion of the store it will be a big performance loss 

const store = subscribe((store) =>store);

const cartItems = store.cart.item;

>SO when you write like this(above) so basically this store variable is subscribed to the redux store whenever
 anything changes inside the store your cart component get to know,
 i.e the store variable will be uodated whenever anything changes in the store and whole store so we dont want 
 the update of whole store.
> suppose if the user logged in it has nothing to do with cart so why this this store variable subscribe to that store 

> SO A better performance way is to only subscribe to a specific portion of the store never do this Above
> Always subscribe to a small portion of the store it is very much efficient  

**Why is it named SELECTOR 
>The name is selector because you are selection a portion of the store that's why it is selector.

   const cartItems = useSelector((store) => store.cart.items);

>when you will write like this the cart item will only update when my  store.item changes
 that small item it has nothing to do with anything happing outside the scope 
 it is only subscribe to cart Item 
 
>> Difference between Reducer & Reducers <<
>So when you are creating an app Store here the keyword is Reducer
   
   const appStore = configureStore({
  reducer: {
    cart: cartReducer,
  },
});

>Reducer Because this is one big reducer for the appStore
 and this reducer can have multiple small Reducers
>when we are writing slice we create multiple reducers

   const cartSlice = createSlice({
  name: "cart",
  initialState: {
    items: [],
  },
  reducers: {
    addItem: (state, action) => {
      state.items.push(action.payload);  
    },

> So when you are writing this store (appStore) this is one REDUCER for the whole app and it contain Multiple small reducers
>when you are creating a slice right so there are multiple small reducer function
 that is why this is one reducer function and know as reducers 

>when you are exporting it you are reduced and you are reducing i.e you are exporting a just one reducer from it 
   
   export default cartSlice.reducer;
   
**what is reducer **
>A reducer is nothing but a Combination of different reducers    
>SO this appStore is a combination of small reducers of the slices 
> and this reducer (export default cartSlice.reducer;) is the combination of 
 below reducer function 
 
    
	Const cartSlice = createSlice({
  name: "cart",
  initialState: {
    items: [],
  },
  reducers: {
    addItem: (state, action) => {
       
      state.items.push(action.payload);  
    },
    removeItem: (state) => {
      state.items.pop();   
    },

    clearCart: (state, action) => {
      state.items.length = 0;  
    },
  },
});

export default cartSlice.reducer;

> this above one is the one reducer which is exporting that is why it is reducer

