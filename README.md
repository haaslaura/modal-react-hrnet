# modal-react-laurahaas

**modal-react-laurahaas** is a React component that displays a modal window after a form has been submitted.

## 📦 Installation

Install the package with npm or yarn :

```bash
npm install modal-react-laurahaas
```

or

```bash
yarn add modal-react-laurahaas
```

## 🚀 Use

Here is an example of using the Dialog component in a React application:

```javascript
import React, { useRef } from "react";
import Dialog from "modal-react-laurahaas";
import "./dialog.css"; // You can import your own CSS if necessary

const App = () => {

    /**
     * Toggles the dialog modal open or closed
     */
    const dialogRef = useRef(null)
    const toggleDialog= () => {
        if(!dialogRef.current) {
            return
        }
        dialogRef.current.hasAttribute("open")
            ? dialogRef.current.close()
            : dialogRef.current.showModal()
    }
    
    return (
    <div>
        <form>
            <div>
                <label htmlFor="first-field">First Field</label>
                <input type="text" id="first-field" />
            </div>
            <button className="save-button" type="submit">Save</button>
        </form>
        
        <Dialog toggleDialog={toggleDialog} ref={dialogRef} />
    </div>
  );
};

export default App;
```

## ⚙️ Props disponibles

| Name           | Type        | Description                             |
| -------------- |:-----------:| ---------------------------------------:|
| `toggleDialog` | `function`  | Function to toggle the modal visibility |
| `dialogRef`    | `React ref` | Reference to the dialog element         |

## 🎨 Personnalisation
The dialog.css file can be modified to adapt the style of the modal to your application.

Example :
```css
.modal {
  background: rgba(0, 0, 0, 0.8);
  color: white;
  padding: 20px;
  border-radius: 5px;
}
```

The css classes available are :
- `.modal {}`
- `::backdrop {}`, `.modal-content {}` (text inside the modal)
- `.modal-close-button {}`
- `.modal-close-button:hover {}` (for the hover background color)
- `.modal-close-button::before {}` (the x icon)