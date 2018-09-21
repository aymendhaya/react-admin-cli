## react-admin-cli 

Command Line Interface for [react-admin](https://github.com/marmelab/react-admin/) Framework

## Install

```bash
$ npm install -g react-admin-cli
```

# Create Single Module
>(Note: this cli will take the folder name as same as resource name. That will make things look simpler and better)
```
$ra create first_module add List sources id firstname lastname
```

 Console Output:
```
|--first_module
        |-- index.js
        |-- List.js

            /// COPY THIS RESULT TO YOU MAIN MODULE ///





            import FirstModule from 'path/to/first_module';

            <Resource name="first_module" list={FirstModule.List} />
```

 first_module/List.js

```jsx
import React from 'react';
import {
  List,
  Datagrid,
  TextField,
} from 'react-admin';

export default props => (
  <List {...props} >
        <Datagrid>
          <TextField source="id" />
          <TextField source="firstname" />
          <TextField source="lastname" />
        </Datagrid>
  </List>
);
```
 first_module/index.js

```js
import List from './List';

export default { List };
```

 App.js (Or index.js)

```js
// This section should be added manually

import FirstModule from './components/first_module';

    <Resource
      name="first_module"
      list={FirstModule.List}
    />
```

# Create Multiple Modules

```
 $ra create second_module add List Create Edit sources id firstname lastname
```

 Result:
```
|--second_module
        |-- Create.js
        |-- index.js
        |-- Edit.js
        |-- List.js

            /// COPY THIS RESULT TO YOU MAIN MODULE ///





            import SecondModule from 'path/to/second_module';

            <Resource name="second_module" list={SecondModule.List} edit={SecondModule.Edit} create={SecondModule.Create} />
```

 second_module/List.js

```jsx
import React from 'react';
import {
  List,
  Datagrid,
  TextField
} from 'react-admin';

export default props => (
  <List {...props} >
        <Datagrid>
          <TextField source="id" />
          <TextField source="firstname" />
          <TextField source="lastname" />
          <EditButton basePath="second_module" />
        </Datagrid>
  </List>
);
```

second_module/Create.js

```jsx
import React from 'react';
import {
  Create,
  TextInput,
  SimpleForm
} from 'react-admin';

export default props => (
  <Create {...props} >
    <SimpleForm>
        <TextInput source="id" />
        <TextInput source="firstname" />
        <TextInput source="lastname" />
    </SimpleForm>
  </Create>
);
```

second_module/Edit.js

```jsx
import React from 'react';
import {
  Edit,
  TextInput,
  SimpleForm
} from 'react-admin';

export default props => (
  <Edit {...props} >
    <SimpleForm>
        <TextInput source="id" />
        <TextInput source="firstname" />
        <TextInput source="lastname" />
    </SimpleForm>
  </Edit>
);
```
 second_module/index.js

```js
import List from './List';
import Create from './Create';
import Edit from './Edit';

export default { List, Create, Edit };
```

 App.js (Or index.js)

```js
// This section should be added manually

import SecondModule from './components/second_module';

    <Resource
      name="second_module"
      list={SecondModule.List}
      create={SecondModule.Create}
      edit={SecondModule.Edit}
    />
```
