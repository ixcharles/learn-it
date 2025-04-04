
# Composants d'Interface Utilisateur et Stylisation dans React

## Introduction
Ce cours présente divers composants d'interface utilisateur et solutions de stylisation couramment utilisés dans les applications React. Vous découvrirez des bibliothèques et des frameworks populaires qui facilitent la création d'interfaces utilisateur réactives, dynamiques et personnalisables.

## Table des Matières
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
Material-UI est un framework d'interface utilisateur React largement adopté, offrant un ensemble complet de composants personnalisables basés sur les directives Material Design de Google.

### Exemple :
```jsx
import { Button } from '@mui/material';

function App() {
  return <Button variant="contained" color="primary">Click Me</Button>;
}
```
Material-UI fournit une grande variété de composants pré-construits hautement personnalisables à l'aide de props.

---

## Styled Components
Styled Components est une bibliothèque qui vous permet d'écrire du CSS directement dans votre JavaScript pour styliser vos composants, offrant des stylesScoped et dynamiques.

### Exemple :
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
Styled Components vous aide à maintenir les stylesScoped au composant et permet une stylisation dynamique via les props.

---

## Emotion
Emotion est une bibliothèque rapide et flexible pour écrire du CSS dans JavaScript, offrant un haut niveau de performance et une facilité d'utilisation pour la stylisation des composants React.

### Exemple :
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
Emotion prend en charge à la fois la syntaxe styled-components et la syntaxe CSS traditionnelle, offrant une flexibilité dans la stylisation.

---

## React Bootstrap
React Bootstrap est une implémentation spécifique à React du framework Bootstrap populaire, fournissant des composants réactifs et personnalisables.

### Exemple :
```jsx
import { Button } from 'react-bootstrap';

function App() {
  return <Button variant="primary">React Bootstrap Button</Button>;
}
```
React Bootstrap remplace jQuery par React, ce qui facilite l'intégration avec l'architecture basée sur les composants de React.

---

## React Icons
React Icons est une bibliothèque simple et personnalisable d'icônes SVG pour React, conçue pour être légère et évolutive.

### Exemple :
```jsx
import { FaBeer } from 'react-icons/fa';

function App() {
  return <h3>Allons prendre une <FaBeer /> !</h3>;
}
```
React Icons fournit des icônes SVG faciles à utiliser et évolutives qui peuvent être personnalisées à l'aide de CSS ou de styles en ligne.

---

## React Datepicker
React Datepicker est un composant de sélecteur de date personnalisable pour React avec diverses fonctionnalités telles que la sélection de date, la sélection de plage et les champs de saisie personnalisés.

### Exemple :
```jsx
import DatePicker from 'react-datepicker';
import 'react-datepicker/dist/react-datepicker.css';

function App() {
  return <DatePicker selected={new Date()} onChange={(date) => console.log(date)} />;
}
```
React Datepicker offre un large éventail d'options de personnalisation, y compris le formatage de la date, la sélection de plage et la localisation.

---

## React Select
React Select est un composant de liste déroulante/sélection flexible et personnalisable, offrant des fonctionnalités telles que la recherche, la multi-sélection et le rendu d'options personnalisées.

### Exemple :
```jsx
import Select from 'react-select';

const options = [{ value: 'chocolate', label: 'Chocolate' }, { value: 'strawberry', label: 'Strawberry' }];

function App() {
  return <Select options={options} />;
}
```
React Select permet des fonctionnalités avancées telles que le rendu d'options personnalisées et le chargement asynchrone des options.

---

## React Table
React Table est un composant de tableau hautement personnalisable qui prend en charge des fonctionnalités telles que le tri, le filtrage, la pagination et le regroupement.

### Exemple :
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
React Table fournit des hooks de bas niveau pour permettre une flexibilité et des performances maximales dans la gestion des interactions complexes de tableaux.

---

## Conclusion

### Points Clés à Retenir :
1. **Material-UI** fournit des composants pré-construits suivant Material Design, qui sont faciles à personnaliser.
2. **Styled Components** et **Emotion** offrent tous deux des solutions CSS-in-JS avec une stylisation dynamique, améliorant la flexibilité de la stylisation dans React.
3. **React Bootstrap** offre un moyen pratique d'implémenter des composants réactifs et personnalisables à l'aide de Bootstrap.
4. **React Icons** fournit des icônes SVG évolutives pour React, personnalisables avec des styles.
5. **React Datepicker** et **React Select** offrent des éléments de formulaire hautement personnalisables, tels que des sélecteurs de date et des listes déroulantes, avec des fonctionnalités puissantes.

### Exercice Pratique :
1. Choisissez une bibliothèque de composants d'interface utilisateur (par exemple, Material-UI ou React Bootstrap) et construisez un formulaire avec des champs de saisie, un bouton de soumission et une validation.
2. Utilisez **React Select** pour remplacer l'un des champs de saisie par une sélection déroulante. Ajoutez une stylisation personnalisée avec **Styled Components** ou **Emotion**.
