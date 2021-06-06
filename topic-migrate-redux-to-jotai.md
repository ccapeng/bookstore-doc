# Migrate Django to Flask

## With Redux
There are really a lot of codes. Dig in each files to check the detail.
- reducers
  - [rootReducer.js](https://github.com/ccapeng/bookstore-hook-redux/blob/master/src/reducers/rootReducer.js)
  - [category.js](https://github.com/ccapeng/bookstore-hook-redux/blob/master/src/reducers/category.js)

- actions [category.js](https://github.com/ccapeng/bookstore-hook-redux/blob/master/src/actions/category.js)

- component [category.js](https://github.com/ccapeng/bookstore-hook-redux/blob/master/src/components/category/Category.js)
  ```
    import { useSelector, useDispatch } from "react-redux";
    import { setCategory, initCategory, setCategoryName, setCategoryStatus } from '../../actions/category';

    const Category = props => {

      const { category, status } = useSelector(state => {
        return state.category
      });
      
      const dispatch = useDispatch();
      
      dispatch(...);
      dispatch(...);
      dispatch(...);
      ...
      
    }
  ```
- Provider with store to wrap around [App](https://github.com/ccapeng/bookstore-hook-redux/blob/master/src/App.js).  
  ```
    <Provider store={store}>
      <App />
    </Provider>
  ```


## With Jotai
It's much simple. I only initialize the default state value, then just call with `useAtom()`
Basically, both reducers and actions are not necessary any more.
- Define store [category.js](https://github.com/ccapeng/bookstore-jotai/blob/main/src/store/category.js)
  ```
    import { atom } from "jotai";

    const initialCategoryListState = []

    export const initialCategoryState = {
        id: 0,
        name: "",
        status: ""
    }

    export const categoryListAtom = atom(initialCategoryListState)
    export const categoryAtom = atom(initialCategoryState)
  ```

- State in the component [Category.js](https://github.com/ccapeng/bookstore-jotai/blob/main/src/components/category/Category.js)
  ```
    import { useAtom } from "jotai";
    import { categoryAtom, initialCategoryState } from "../../store/category";

    const Category = props => {

    const [category, setCategory] = useAtom(categoryAtom);
    ...
    }
  ```
  