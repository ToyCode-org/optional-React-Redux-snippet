<a href="https://marketplace.visualstudio.com/items?itemName=LEE-YO-HAN.react-redux-optional-snippets">Marketplace</a><span> /</span> <a href="https://github.com/ToyCode-org/optional-React-Redux-snippet/blob/main/docs/docs.md">Usage</a>

# React/Redux optional snippets

### JavaScript and React/Redux snippets

</br></br>

<h4 align="center">🛠 Applicable Tools 🛠</h4>
<div align="center">
    <img src="https://img.shields.io/badge/React-61DAFB?style=flat&logo=React&logoColor=white" />
    <img src="https://img.shields.io/badge/Redux-764ABC?style=flat&logo=Redux&logoColor=white" />
    <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=JavaScript&logoColor=white" />
    <img src="https://img.shields.io/badge/TypeScript-3178C6?style=flat&logo=TypeScript&logoColor=white" />
</div>

</br></br>

# Installation

## Visual Studio Marketplace

</br>

Launch Quick Open:

- macOS: ⌘P
- Windows: Ctrl+P

Paste the following command and press Enter

```
code --install-extension LEE-YO-HAN.react-redux-optional-snippets
```

</br>
</br>

# Current Support Features

Currently, functional components, arrow functions, some react hooks, and Provides a store for the Reader's Toolkit, a slice template (with AsyncThunk).
In the future, we will update snippets and templates that can minimize repetitive tasks and various versions such as saga.

ps. this snippets is best used with ES7+ React/Redux/React-Native/JS snippets

<br>

Here's how to use it.

<br>

## for functions

```javascript
// type edcf
export default function Name() {
  return (
    <div>
      <p>new Component</p>
    </div>
  );
}
```

```javascript
// type ecf
export const Name = () => {
  return (
    <div>
      <p>new Component</p>
    </div>
  );
};
```

```javascript
// type caf
const Name = () => {};
```

For a function snippets, you just need to type a function name after type a keyword.

<br><br>

## for React Hooks

```javascript
// type urr
const name = useRef();
```

```javascript
// type uss
const [name, setname] = useState();
```

```javascript
// type uff
useEffect(() => {}, []);
```

```javascript
// type ucc
useCallback(() => {}, []);
```

```javascript
// type umm
useMemo(() => {}, []);
```

For useState and useRef also you just need to type a function name after type a keyword.

<br><br>

## for Redux Template

```javascript
// rdxstore
import { configureStore } from "@reduxjs/toolkit";

const store = configureStore({
  reducer: {},
});
export default store;
```

```javascript
// rdxslice
// first focus is action's name
// second focus is Slice name
// After type the action name, press the TAB button and type the slice name.
import { createAsyncThunk, createSlice } from "@reduxjs/toolkit";

export const getnameAll = createAsyncThunk(
  "GET_ALL",
  async (payload, thunkAPI) => {
    try {
      // const { data } = await request API
      return thunkAPI.fulfillWithValue(data);
    } catch (error) {
      return thunkAPI.rejectWithValue(error);
    }
  }
);

export const getnameOne = createAsyncThunk(
  "GET_ONE",
  async (payload, thunkAPI) => {
    try {
      // const { data } = await request API
      return thunkAPI.fulfillWithValue(data);
    } catch (error) {
      return thunkAPI.rejectWithValue(error);
    }
  }
);

export const addname = createAsyncThunk(
  "POST_ADD",
  async (payload, thunkAPI) => {
    try {
      // const { data } = await request API
      return thunkAPI.fulfillWithValue(data);
    } catch (errer) {
      return thunkAPI.rejectWithValue(errer);
    }
  }
);

export const updatename = createAsyncThunk(
  "POST_UPDATAE",
  async (payload, thunkAPI) => {
    try {
      // const { data } = await request API
      return thunkAPI.fulfillWithValue(data);
    } catch (error) {
      return thunkAPI.rejectWithValue(error);
    }
  }
);

export const deletename = createAsyncThunk(
  "DELETE_ONE",
  async (payload, thunkAPI) => {
    try {
      // await delete request API
      return thunkAPI.fulfillWithValue(payload);
    } catch (error) {
      return thunkAPI.rejectWithValue(error);
    }
  }
);

/* InitialState */
// data, isLoading, error로 상태관리
const initialState = {
  name: [],
  isLoading: false,
  error: null,
};

export const nameSlice = createSlice({
  name: "name",
  initialState,
  reducers: {},
  extraReducers: (builder) => {
    builder.addCase(getnameAll.fulfilled, (state, action) => {
      state.name = action.payload;
    });
    builder.addCase(getnameOne.fulfilled, (state, action) => {
      state.name = action.payload;
    });
    builder.addCase(addname.fulfilled, (state, action) => {
      // state.name.unshift(action.payload);
    });
    builder.addCase(updatename.fulfilled, (state, action) => {
      const newState = state.name.map((item) =>
        action.meta.arg.id === item.id
          ? {
              ...action.payload,
            }
          : item
      );
      state.name = newState;
    });
    builder.addCase(deletename.fulfilled, (state, action) => {
      const newState = state.name.filter((item) => item.id !== action.payload);
      state.name = newState;
    });
  },
});

export default nameSlice.reducer;
```
