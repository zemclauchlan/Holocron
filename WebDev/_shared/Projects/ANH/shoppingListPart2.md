
# Previous Weeks Solution
If you struggled with the creation of the tables, model and forms, use the code in this section to create.
## Database Tables

```sql
CREATE TABLE shopping_lists(  
    id INTEGER NOT NULL PRIMARY KEY AUTOINCREMENT,
    name TEXT NOT NULL,
    userID INTEGER NOT NULL
);

CREATE TABLE shopping_item(  
    id INTEGER NOT NULL PRIMARY KEY AUTOINCREMENT,
    name TEXT NOT NULL
);

CREATE TABLE shopping_list_items(  
    id INTEGER NOT NULL PRIMARY KEY AUTOINCREMENT,
    shoppingListID INTEGER NOT NULL,
    shoppingItemID INTEGER NOT NULL,
    quantity INTEGER NOT NULL,
    completed BOOLEAN NOT NULL
);
```
Your database should create the tables shown:
![shoppingListDB](/WebDev/_shared/Projects/ANH/images/shoppingListDB.png)


## `models.py`
```python
class ShoppingLists(db.Model):
    id = db.Column(db.Integer, primary_key=True, autoincrement=True)
    userID = db.Column(db.Integer)
    name = db.Column(db.String(255))

class ShoppingItem(db.Model):
    id = db.Column(db.Integer, primary_key=True, autoincrement=True)
    name = db.Column(db.String(255))

class ShoppingListItems(db.Model):
    id = db.Column(db.Integer, primary_key=True, autoincrement=True)
    shoppingListID = db.Column(db.Integer)
    shoppingItemID = db.Column(db.Integer)
    quantity = db.Column(db.Integer)
    complete = db.Column(db.Boolean)

```

## forms

```python
class ShoppingListForm(FlaskForm):
    name = StringField("Name", validators=[DataRequired()])
    submit = SubmitField("Submit List")

class ShoppingListItemForm(FlaskForm):
    item_name = StringField("Item Name", validators=[DataRequired()])
    submit = SubmitField("Submit Item")
```



# This week focus

Create the Shopping Lists, not items.

Assessment / Documentation heavy week