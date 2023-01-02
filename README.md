[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-c66648af7eb3fe8bc4f294546bfd86ef473780cde1dea487d3c4ff354943c9ae.svg)](https://classroom.github.com/online_ide?assignment_repo_id=9649608&assignment_repo_type=AssignmentRepo)

items_in_stock = [
    {
        "Item_id": 0,
        "Item_name": "Toblerone",
        'Item_price': 9
    },
    {
        "Item_id": 1,
        "Item_name": "Coke-Cola",
        'Item_price': 2
    },
    {
        "Item_id": 2,
        "Item_name": "Lays-Salted",
        'Item_price': 1
    },
    {
        "Item_id": 3,
        "Item_name": "Lays-Chilli",
        'Item_price': 2
    },
    {
        "Item_id": 4,
        "Item_name": "Lays-Tomato Ketchup",
        'Item_price': 3
    },
    {
        "Item_id": 5,
        "Item_name": "Pepsi",
        "Item_price": 4
    },
    {
        "Item_id":6,
        "Item_name": "Vimto- Fruit Flavoured Juice",
        "Item_price": 2
    },
    {
       "Item_id":7,
       "Item_name": "Galaxy Smooth Milk Chocolate",
       "Item_price": 5
    },
    {
        "Item_id":8,
        "Item_name":"Sprite",
        "Item_price": 3
    },
    {
        "Item_id": 9,
        "Item_name": "Eurocake Chocolate Chip Brownie",
        "Item_price": 3
    },
    {
        "Item_id": 10,
        "Item_name":"Oreo",
        "Item_price": 2
    }
]


item = []

receipt = """
\t\tPRODUCT -- PRICE
"""

sum = 0

run = True

print("------- Julisha's Vending Machine-------\n\n")
print("----------The Items In the Vending Machine Are----------\n\n")

for i in items_in_stock:
    print(f"PRODUCT: {i['Item_name']} - PRICE: {i['Item_price']} - PRODUCT ID: {i['Item_id']}")


def vending_machine(items_in_stock, run, item):
    while run:

        brought_item = int(input("\n\nENTER THE ITEM CODE OF THE PRODUCT YOU WANT TO BUY: "))

        if brought_item < len(items_in_stock):
            item.append(items_in_stock[brought_item])
        else:
            print("The PRODUCT ID is wrong.")

        more_than_one_item = str(input("PRESS ANY KEY TO ADD MORE ITEMS AND PRESS Q TO QUIT. "))

        if more_than_one_item == "Q":
            run = False

    rec = int(input(("1. Print the receipt 2. Only print the total sum  ")))
    if rec == 1:
        print(make_receipt(item, receipt))
    elif rec == 2:
        print(sum(item))
    else:
        print("INVALID ENTRY")


def sum(item):
    sum = 0

    for i in item:
        sum += i["Item_price"]

    return sum

def make_receipt(item, receipt):

    for i in item:
        receipt += f"""
        \t{i["Item_name"]} -- {i['Item_price']}
        """

    receipt += f"""
        \tTotal --- {sum(item)}
        
        
        """
    return receipt


if __name__ == "__main__":
    vending_machine(items_in_stock, run, item)
    