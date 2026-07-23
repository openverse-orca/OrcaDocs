# How to use Undo and Redo?

## Question
When building or editing scenes in OrcaLab, I sometimes accidentally perform incorrect operations. Can I undo these operations? If I undo too far, can I restore previous operations?

## Answer

The OrcaLab client provides standard **Undo** and **Redo** functionality to help users correct mistakes during scene building and editing. This is a very important feature in 3D software that greatly improves work efficiency and error tolerance.

## 📋 Using Undo and Redo

### 1. **Via the Menu Bar**

OrcaLab's top menu bar typically provides an "Edit" option containing "Undo" and "Redo" functionality.

-   **Undo**:
    -   Click "Edit" menu → "Undo."
    -   **Shortcut**: `Ctrl + Z`.
-   **Redo**:
    -   Click "Edit" menu → "Redo."
    -   **Shortcut**: `Ctrl + Shift + Z`.

### 2. **Keyboard Shortcuts (Recommended)**

Using keyboard shortcuts is the most efficient way to undo and redo, as it allows you to quickly correct mistakes without leaving your current workspace.

-   **Undo**: Press `Ctrl + Z`.
-   **Redo**: Press `Ctrl + Shift + Z`.

#### Example: Undo Object Movement
1.  You dragged and moved an object in OrcaLab.
2.  You realize the position is wrong and press `Ctrl + Z`.
3.  The object immediately returns to its position before the move.

#### Example: Redo Object Movement
1.  You moved object A, then moved object B.
2.  You undid the move of object B. Now you want to restore the move of object B.
3.  Press `Ctrl + Shift + Z`.
4.  Object B returns to its moved position.

## 💡 How Undo/Redo Works

OrcaLab maintains an operation history stack. Whenever you perform an undoable operation in the scene (such as moving an object, changing a property, deleting, etc.), that operation is recorded in the history stack.
-   **Undo**: Pops the most recent operation from the history stack and executes its reverse.
-   **Redo**: Pushes the most recently undone operation back onto the history stack and executes it again.

## ⚠️ Important Notes

### 1. **History Limit**
-   Most software's undo/redo history is not infinite; there is typically a maximum step limit.
-   Once the limit is exceeded, the earliest operations are cleared and can no longer be undone.

### 2. **Operation Granularity**
-   The granularity of undo/redo depends on the software's design. Typically, a single mouse drag or one property input is treated as one operation.

### 3. **Non-Undoable Operations**
-   Certain operations may not be undoable. For example, **saving a file** is typically not undoable. If you saved an incorrect state, you won't be able to undo back to the pre-save state. Therefore, **frequent saving and using "Save As" for backups** is a very good habit.
-   **Deleting files** (at the operating system level) is also typically not undoable.

### 4. **Undo Across Different Tools**
-   The OrcaLab client's undo/redo functionality primarily targets its GUI operations. If you modify the scene through a Python script, the script's execution may be treated as a single operation, or the script itself may need to implement undo logic.

### 5. **Save & Undo Interaction**
-   After completing a series of operations and being satisfied, save your layout promptly (Ctrl+S). This "cements" the current state. Even if you make mistakes afterward, as long as you haven't saved again, you can exit without saving and reload the file to return to the last saved state.

## 📝 Summary

OrcaLab's Undo (`Ctrl + Z`) and Redo (`Ctrl + Shift + Z`) functionality is an important safeguard during scene building and editing. Mastering their use will help you create and debug more confidently and efficiently. Also, pay attention to save timing and history limits to ensure data safety.

## Related Links
- [OrcaLab Basic Operation Guide](user-guide/orca-lab-basic-operation-guide-v1.0.md)
- [What are the components of the OrcaLab interface?](FAQ-list/061-what-are-the-components-of-the-orcalab-interface.md)
- [How to save and load custom layouts?](FAQ-list/070-how-to-save-and-load-custom-layouts.md)
- [What are the keyboard shortcuts and how to customize them?](FAQ-list/071-what-are-the-shortcuts-and-how-to-customize-them.md)