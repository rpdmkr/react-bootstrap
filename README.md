wolox-react-bootstrap
==================

## Prerequisites

- [React](https://facebook.github.io/react/docs/getting-started.html)

- [Node (minimum version: 6.2.0) and npm](https://github.com/creationix/nvm#install-script)

- [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)


## TL;DR

You don't need to clone this repository. Just follow this steps:

1- Run the following command:

```
bash <(curl -s https://raw.githubusercontent.com/Wolox/react-bootstrap/development/run.sh) [--verbose]
```

2- Search for TODO commented lines and follow the instructions. (Search "// TODO")

3- Add .env file with your API_BASE_URL

## Components

This are the components you can to choose for your app.
* SearchBar
* TextArea
* Field
* Spinner

### SearchBar

The component contain this props:
* className
* formClassName
* buttonClassName
* textButtonSearch
* children
* handleSubmit

Should be called this way.

````
<SearchBar handleSubmit={this.onSubmit}> 
  <label className="Label-search">
    Name:
    <input name="name" id="name" type="input" onChange={this.onChange}/>
  </label>
  <label className="Label-search">
    Last Name:
    <input name="lastName" id="lastName" type="input" onChange={this.onChange}/>
  </label>
</SearchBar>
````

If you decided to use redux-form you must add it to the component and use it in this way.

```
<SearchBar
  onSubmit={handleSubmit}
  className={styles.userFormContainer}
  formClassName={styles.userForm}
>
  <div className={styles.search}>
    <Field
      component={Input}
      name="name"
      placeholder={i18next.t('SearchUser:namePlaceholder')}
      type="text"
    />
     <Field
      component={Input}
      name="brand"
      placeholder={i18next.t('SearchUser:brandPlaceholder')}
      type="text"
    />
    <Field
      component={Select}
      name="status"
      dataOptions={STATES}
      placeholder={i18next.t('SearchUser:statusPlaceholder')}
    />
  <div>
</SearchBar
```

### Field

The component only use with redux-form, contain this props.
* input

Use it in this way:

```
input = wrapField(Input);

<Field
  name={fieldName}  
  type="text"
  component={this.input}
  className={styles.input}
/>
```

### Spinner

The component contain this props:
* WrappedComponent
* classNameContainer
* classNameLoading
* idLoading
* colorSpinner

Contain this component:
* Loading 
  * className
  * id
  * colorSpinner


In the example we will use it with the SearchBar component.

```
src/components/SearchBar

//Import into the component to be used.
import { withSpinner } from '../Spinner';

//Include in the definition of the component to be used. In this case is SearchBar.
export default withSpinner({
  WrappedComponent: SearchBarContainer,
  idLoading: 1,
  classNameContainer: styles.spinner
});

```

Here you can see all the spinner models that this library has http://kyleamathews.github.io/react-spinkit/
