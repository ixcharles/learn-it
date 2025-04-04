
# TypeScript Mastery in Next.js Projects

A deep dive into advanced TypeScript concepts for building scalable and type-safe applications in Next.js, focusing on advanced patterns, state management, and API integration.

---

## Table of Contents

- [Advanced TypeScript in React](#advanced-typescript-in-react)  
  - [Type Inference](#type-inference)  
  - [Enums, Unions, Intersections](#enums-unions-intersections)  
  - [Utility Types](#utility-types)  
- [Typed API Routes](#typed-api-routes)  
  - [Creating API Routes](#creating-api-routes)  
  - [Typing Request and Response](#typing-request-and-response)  
- [Reusable Component Types](#reusable-component-types)  
  - [Custom Type Definitions](#custom-type-definitions)  
  - [Polymorphic Components](#polymorphic-components)  
- [Handling Forms and Events](#handling-forms-and-events)  
  - [Typing Form Elements and Events](#typing-form-elements-and-events)  
  - [Controlled vs Uncontrolled Inputs](#controlled-vs-uncontrolled-inputs)  
- [Managing State with TypeScript](#managing-state-with-typescript)  
  - [useState and useReducer with Types](#usestate-and-usereducer-with-types)  
  - [useContext with Custom Types](#usecontext-with-custom-types)  

---

## Advanced TypeScript in React

### Type Inference  
TypeScript automatically infers types for variables, function return values, and parameters.

**Example:**
```ts
let name = "John";  // inferred as string
const sum = (a: number, b: number) => a + b;  // inferred return type: number
```

### Enums, Unions, Intersections  
Enums define a set of named constants. Unions combine multiple types, and intersections combine types.

**Example:**
```ts
enum Status { Pending, InProgress, Completed }

type User = { name: string; age: number };
type Admin = User & { role: string };
type AdminUser = Admin | { guest: boolean };
```

### Utility Types  
Utility types like `Partial`, `Pick`, and `Record` enable transformation of types.

**Example:**
```ts
type Person = { name: string; age: number };
type PartialPerson = Partial<Person>;  // all properties are optional
type NameOnly = Pick<Person, "name">;  // only "name" is required
type RecordType = Record<string, number>;  // object with string keys and number values
```

---

## Typed API Routes

### Creating API Routes  
Next.js API routes are defined in the `/pages/api` directory.

**Example:**
```tsx
// pages/api/user.ts
import { NextApiRequest, NextApiResponse } from 'next';

export default (req: NextApiRequest, res: NextApiResponse) => {
  res.status(200).json({ name: "John" });
};
```

### Typing Request and Response  
Type the `NextApiRequest` and `NextApiResponse` for API endpoints.

**Example:**
```tsx
// pages/api/login.ts
import { NextApiRequest, NextApiResponse } from 'next';

type Data = { message: string; success: boolean };

export default (req: NextApiRequest, res: NextApiResponse<Data>) => {
  res.status(200).json({ message: "Login successful", success: true });
};
```

---

## Reusable Component Types

### Custom Type Definitions  
Define types for custom components for better reusability and scalability.

**Example:**
```ts
type ButtonProps = { label: string; onClick: () => void };

const Button: React.FC<ButtonProps> = ({ label, onClick }) => (
  <button onClick={onClick}>{label}</button>
);
```

### Polymorphic Components  
Polymorphic components accept different types of elements based on props, enabling flexible UI elements.

**Example:**
```ts
type BoxProps<T extends React.ElementType> = {
  as?: T;
  children: React.ReactNode;
};

function Box<T extends React.ElementType>({ as: Component = 'div', children }: BoxProps<T>) {
  return <Component>{children}</Component>;
}

// Usage
<Box as="section">This is a section</Box>
```

---

## Handling Forms and Events

### Typing Form Elements and Events  
Properly type form elements and their event handlers.

**Example:**
```tsx
const handleSubmit = (event: React.FormEvent<HTMLFormElement>) => {
  event.preventDefault();
  console.log("Form submitted");
};

return <form onSubmit={handleSubmit}>Submit</form>;
```

### Controlled vs Uncontrolled Inputs  
Controlled inputs have their value managed by React state, while uncontrolled inputs are managed by the DOM.

**Example:**
```tsx
// Controlled Input
const [value, setValue] = useState<string>('');
const handleChange = (e: React.ChangeEvent<HTMLInputElement>) => setValue(e.target.value);

return <input value={value} onChange={handleChange} />;

// Uncontrolled Input
const inputRef = useRef<HTMLInputElement>(null);
return <input ref={inputRef} />;
```

---

## Managing State with TypeScript

### useState and useReducer with Types  
Both hooks can benefit from type annotations for better state management.

**Example:**
```tsx
const [count, setCount] = useState<number>(0);

const [state, dispatch] = useReducer(
  (state: number, action: { type: string; payload: number }) => {
    switch (action.type) {
      case 'increment': return state + action.payload;
      default: return state;
    }
  },
  0
);
```

### useContext with Custom Types  
Use `useContext` with custom types to create type-safe global state management.

**Example:**
```tsx
type AppContextType = { user: string; setUser: (name: string) => void };
const AppContext = createContext<AppContextType | undefined>(undefined);

const MyComponent = () => {
  const context = useContext(AppContext);
  if (!context) throw new Error('useContext must be used within a provider');
  return <div>{context.user}</div>;
};
```

---

## Conclusion

**Key Takeaways:**
- Advanced TypeScript features like enums, unions, and utility types make code more robust and flexible.
- Properly typing API routes ensures better security and reliability.
- Polymorphic components enhance component reusability and flexibility.
- Correctly typing forms and events ensures a smoother developer experience and fewer bugs.
- Managing state with TypeScript brings clarity and maintainability to complex applications.

---

## Practical Exercise

**Build a Typed Form with State Management:**
1. Create a form with `name` and `email` fields.
2. Use `useState` to manage the form's input state, and type it with `string`.
3. Create a submit function that prints the form data to the console.
4. Add a controlled input for `name` and `email`, ensuring proper event typing.
