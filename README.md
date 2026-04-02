# QuantityMeasurementApp-Frontend🌿

A simple web app to **compare**, **convert**, and do **arithmetic** on different units of measurement like Length, Weight, Temperature and Volume.

---

## 📁 Project Structure

```
QuantityMeasurementApp-Frontend/
│
├── index.html          # Login & Signup page
├── dashboard.html      # Main app page
│
├── css/
│   ├── auth.css        # Styles for login/signup page
│   └── dashboard.css   # Styles for main app page
│
└── js/
    ├── auth.js         # Logic for login/signup
    └── dashboard.js    # Logic for main app
```

---

## Pages

### 1. `index.html` — Login & Signup Page

First page the user sees. Has two tabs — **Login** and **Signup**.

**Login Tab:**
- Email input
- Password input (with show/hide eye icon)
- Login button
- Link to switch to Signup

**Signup Tab:**
- Full Name input
- Email input
- Password input (with show/hide eye icon)
- Mobile Number input (only 10 digits allowed)
- Signup button
- Link to switch to Login

**Validation Rules:**
- Email must be in valid format (e.g. `example@mail.com`)
- Password must have at least 6 characters, one uppercase, one lowercase, and one special character (`@#$%^&+=!`)
- Mobile must be exactly 10 digits
- Red error messages appear below invalid fields
- On success → redirected to `dashboard.html`

**Data Storage:**
- User info saved in `localStorage` under key `qm_user`

---

### 2. `dashboard.html` — Main App Page

Header with app name and a **Logout** button. Two main sections:

**Section 1 — Choose Type** (4 clickable cards):

| Card | Type |
|------|------|
| 📏 | Length |
| ⚖️ | Weight |
| 🌡️ | Temperature |
| 🧴 | Volume |

> Selected card gets a teal border. Hovered card gets a blue border.

**Section 2 — Choose Action** (3 equal-width buttons):

| Action | Description |
|--------|-------------|
| Comparison | Compare two values |
| Conversion | Convert one unit to another |
| Arithmetic | Add, subtract, multiply or divide two values |

> Active button turns blue.

---

## Panels

### Comparison Panel
- Two inputs side by side — **FROM** and **TO**
- Each has a number input and a unit dropdown
- Result box shows which value is greater / less / equal
- Result box has a unit dropdown to choose display unit

**Example:** `1 Kilometer > 500 Meter`

---

### Conversion Panel
- One input on the left (**VALUE**) with unit dropdown
- Arrow `→` in the middle
- Unit dropdown on the right (**CONVERT TO**)
- Result box shows the converted value

**Example:** `1 Kilometer = 1000 Meter`

---

### Arithmetic Panel
- Two inputs side by side — **Value 1** and **Value 2**
- Each has a number input and a unit dropdown
- Operator dropdown in the middle (`+`, `−`, `×`, `÷`)
- Result box has a unit dropdown to choose display unit

**Example:** `1 Kilometer + 1 Kilometer = 2 Kilometer`

---

## Measurement Types & Units

### Length *(base: Meter)*

| Unit | Factor (in Meters) |
|------|--------------------|
| Kilometer | 1000 |
| Meter | 1 |
| Centimeter | 0.01 |
| Millimeter | 0.001 |
| Mile | 1609.34 |
| Foot | 0.3048 |
| Inch | 0.0254 |

### Weight *(base: Kilogram)*

| Unit | Factor (in Kilograms) |
|------|-----------------------|
| Kilogram | 1 |
| Gram | 0.001 |
| Milligram | 0.000001 |
| Pound | 0.453592 |
| Ounce | 0.0283495 |
| Tonne | 1000 |

### Temperature

| Unit | Method |
|------|--------|
| Celsius | Formula-based conversion |
| Fahrenheit | Formula-based conversion |
| Kelvin | Formula-based conversion |

> Temperature does not use a simple factor — it uses dedicated conversion formulas.

### Volume *(base: Liter)*

| Unit | Factor (in Liters) |
|------|--------------------|
| Liter | 1 |
| Milliliter | 0.001 |
| Gallon | 3.78541 |
| Cup | 0.236588 |
| Tablespoon | 0.0147868 |

---

## JavaScript Files

### `auth.js`

| Function | Description |
|----------|-------------|
| `switchTab(tab)` | Switches between Login and Signup tabs |
| `togglePw(inputId, icon)` | Shows or hides password text |
| `isValidEmail(email)` | Checks if email format is correct |
| `setError(errId, inputId, show)` | Shows or hides error message for a field |
| `clearAllErrors()` | Clears all error messages |
| `doLogin()` | Validates login form and redirects to dashboard |
| `doSignup()` | Validates signup form and redirects to dashboard |

### `dashboard.js`

| Function | Description |
|----------|-------------|
| `selectType(type)` | Changes the measurement type |
| `selectAction(action)` | Switches between Comparison, Conversion, Arithmetic |
| `populateSelects(type)` | Fills all dropdowns with units for selected type |
| `fillDropdown(id, units, selected)` | Fills a single dropdown with options |
| `compute()` | Calls the right compute function based on current action |
| `computeComparison()` | Calculates and shows comparison result |
| `computeConversion()` | Calculates and shows conversion result |
| `computeArithmetic()` | Calculates and shows arithmetic result |
| `convertUnits(value, from, to, type)` | Converts a value from one unit to another |
| `convertTemp(val, from, to)` | Converts temperature values using formulas |
| `formatNum(n)` | Formats a number to clean readable format |
| `logout()` | Clears user session and goes back to login page |

---

## CSS Files

### `auth.css`

| Class | Purpose |
|-------|---------|
| `.card` | White box in the center of the page |
| `.brand` | Blue left side with logo and app name |
| `.form-section` | Right side with the form |
| `.tabs` | Login/Signup tab buttons |
| `.form-panel` | Login or signup form (only active one shown) |
| `.field` | Each input group (label + input + error) |
| `.error-msg` | Red error text below inputs (hidden by default) |
| `.error-msg.show` | Makes the error message visible |
| `.btn-submit` | The blue Login/Signup button |
| `.password-wrap` | Wrapper for password input with eye icon |

### `dashboard.css`

| Class | Purpose |
|-------|---------|
| `header` | Blue top bar with app name and logout button |
| `.main` | Main content area |
| `.section-title` | Small uppercase label like "CHOOSE TYPE" |
| `.type-grid` | 4-column grid for type cards |
| `.type-card` | Individual type card |
| `.type-card.active` | Selected card with teal border |
| `.action-row` | Row of 3 action buttons |
| `.action-btn` | Individual action button |
| `.action-btn.active` | Selected button with blue background |
| `.panel` | Each action panel (hidden by default) |
| `.panel.active` | Currently visible panel |
| `.two-col` | Two column layout for inputs |
| `.big-input` | Large number input box |
| `.unit-select` | Unit dropdown below each input |
| `.result-box` | Green left-bordered result area |
| `.result-row` | Result text and unit dropdown side by side |
| `.op-box` | Operator dropdown wrapper in Arithmetic panel |

---

> No server needed. Everything runs in the browser.

---

##  Technologies Used

- HTML
- CSS
- JavaScript (Vanilla, no frameworks)
- Google Fonts (Poppins)
- localStorage (for storing user session)

 [feature/frontend-vanilla-html-css-js](https://github.com/abhishekkushwaha-2003/QuantityMeasurementApp-Frontend/tree/feature/frontend-vanilla-html-css-js)

---







