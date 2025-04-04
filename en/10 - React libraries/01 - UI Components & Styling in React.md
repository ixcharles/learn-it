
# UI Components & Styling in React

## Introduction
This course introduces various UI components and styling solutions commonly used in React applications. You'll learn about popular libraries and frameworks that help create responsive, dynamic, and customizable UIs with ease.

## Table of Contents
1. [Material-UI](#material-ui)
2. [Styled Components](#styled-components)
3. [Emotion](#emotion)
4. [React Bootstrap](#react-bootstrap)
5. [React Icons](#react-icons)
6. [React Datepicker](#react-datepicker)
7. [React Select](#react-select)
8. [React Table](#react-table)
9. [Conclusion](#conclusion)

---

## Material-UI
Material-UI is a widely adopted React UI framework offering a comprehensive set of customizable components based on Google's Material Design guidelines.

### Example:
```jsx
import { Button } from '@mui/material';

function App() {
  return <Button variant="contained" color="primary">Click Me</Button>;
}
```
Material-UI provides a wide variety of pre-built components that are highly customizable using props.

---

## Styled Components
Styled Components is a library that allows you to write actual CSS to style your components in JavaScript, offering scoped, dynamic styles.

### Example:
```jsx
import styled from 'styled-components';

const Button = styled.button`
  background-color: ${(props) => props.bgColor || 'blue'};
  color: white;
  padding: 10px;
`;

function App() {
  return <Button bgColor="green">Styled Button</Button>;
}
```
Styled Components helps you keep the styles scoped to the component and allows dynamic styling via props.

---

## Emotion
Emotion is a fast, flexible library for writing CSS in JavaScript, offering a high level of performance and ease of use for styling React components.

### Example:
```jsx
/** @jsxImportSource @emotion/react */
import { css } from '@emotion/react';

const style = css`
  color: red;
  font-size: 20px;
`;

function App() {
  return <div css={style}>Emotion Styled Text</div>;
}
```
Emotion supports both styled-components syntax and traditional CSS syntax, offering flexibility in styling.

---

## React Bootstrap
React Bootstrap is a React-specific implementation of the popular Bootstrap framework, providing responsive, customizable components.

### Example:
```jsx
import { Button } from 'react-bootstrap';

function App() {
  return <Button variant="primary">React Bootstrap Button</Button>;
}
```
React Bootstrap replaces jQuery with React, making it easier to integrate with React's component-based architecture.

---

## React Icons
React Icons is a simple and customizable library of SVG icons for React, designed to be lightweight and scalable.

### Example:
```jsx
import { FaBeer } from 'react-icons/fa';

function App() {
  return <h3>Let's go for a <FaBeer />!</h3>;
}
```
React Icons provides easy-to-use, scalable SVG icons that can be customized using CSS or inline styling.

---

## React Datepicker
React Datepicker is a customizable date picker component for React with various features such as date selection, range selection, and custom input fields.

### Example:
```jsx
import DatePicker from 'react-datepicker';
import 'react-datepicker/dist/react-datepicker.css';

function App() {
  return <DatePicker selected={new Date()} onChange={(date) => console.log(date)} />;
}
```
React Datepicker offers a wide range of customization options, including date formatting, range selection, and localization.

---

## React Select
React Select is a flexible and customizable dropdown/select component, offering features like searchability, multi-selection, and custom options rendering.

### Example:
```jsx
import Select from 'react-select';

const options = [{ value: 'chocolate', label: 'Chocolate' }, { value: 'strawberry', label: 'Strawberry' }];

function App() {
  return <Select options={options} />;
}
```
React Select enables advanced features like custom option rendering and asynchronous loading of options.

---

## React Table
React Table is a highly customizable table component that supports features like sorting, filtering, pagination, and grouping.

### Example:
```jsx
import { useTable } from 'react-table';

const data = [{ name: 'John', age: 28 }, { name: 'Jane', age: 22 }];
const columns = [{ Header: 'Name', accessor: 'name' }, { Header: 'Age', accessor: 'age' }];

function App() {
  const { getTableProps, getTableBodyProps, headerGroups, rows, prepareRow } = useTable({ columns, data });
  
  return (
    <table {...getTableProps()}>
      <thead>
        {headerGroups.map(headerGroup => (
          <tr {...headerGroup.getHeaderGroupProps()}>
            {headerGroup.headers.map(column => (
              <th {...column.getHeaderProps()}>{column.render('Header')}</th>
            ))}
          </tr>
        ))}
      </thead>
      <tbody {...getTableBodyProps()}>
        {rows.map(row => {
          prepareRow(row);
          return (
            <tr {...row.getRowProps()}>
              {row.cells.map(cell => {
                return <td {...cell.getCellProps()}>{cell.render('Cell')}</td>;
              })}
            </tr>
          );
        })}
      </tbody>
    </table>
  );
}
```
React Table provides low-level hooks to allow for maximum flexibility and performance in handling complex table interactions.

---

## Conclusion

### Key Takeaways:
1. **Material-UI** provides pre-built components following Material Design, which are easy to customize.
2. **Styled Components** and **Emotion** both offer CSS-in-JS solutions with dynamic styling, enhancing the flexibility of styling in React.
3. **React Bootstrap** offers a convenient way to implement responsive and customizable components using Bootstrap.
4. **React Icons** provides scalable SVG icons for React, customizable with styles.
5. **React Datepicker** and **React Select** offer highly customizable form elements, like date pickers and dropdowns, with powerful features.

### Practical Exercise:
1. Choose a UI component library (e.g., Material-UI or React Bootstrap) and build a form with input fields, a submit button, and validation.
2. Use **React Select** to replace one of the input fields with a dropdown selection. Add custom styling with **Styled Components** or **Emotion**.
