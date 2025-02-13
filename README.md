# modal-react-laurahaas

**modal-react-laurahaas** is a React component that displays a modal window after a form has been submitted. The modal will be closed by clicking on the "close" button or by clicking outside the modal. You can customise the form submission function.

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
     * Closes the modal when clicked externally
     */
    const dialogRef = useRef(null)
    const toggleDialog= () => {
        if(!dialogRef.current) {
            return
        }
        dialogRef.current.hasAttribute("open")
            ? dialogRef.current.close()
            : dialogRef.current.showModal();
    };

    /**
     * Customise the function you want to use when sending your form
     */
    const sendingFunction = (e) => {
    e.preventDefault();
    console.log("Information sent!");
    toggleDialog();
    }
    
    return (
    <div>
        <form onSubmit={sendingFunction}>
            <div>
                <label htmlFor="first-field">First Field</label>
                <input type="text" id="first-field" />
            </div>
            <button className="save-button" type="submit">Save</button>
        </form>
        
        <Dialog
            toggleDialog={toggleDialog}
            ref={dialogRef}
            textModal="My modal content"
        />
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
| `textModal`    | `string`    | The text content of your modal          |

&nbsp;
## 🎨 Personnalisation
The dialog.css file can be modified to adapt the style of the modal to your application.

Example :
```css
.hl-modal {
  background: rgba(0, 0, 0, 0.8);
  color: white;
  padding: 20px;
  border-radius: 5px;
}
```

The css classes available are :
- `.hl-modal {}`
- `::backdrop {}`, `.hl-modal-content {}` (text inside the modal)
- `.hl-modal-close-button {}`
- `.hl-modal-close-button:hover {}` (for the hover background color)
- `.hl-modal-close-button::before {}` (the x icon)