def add(l, des, price, stock, ran1, ran2): #adds an item to a list
    i = [des, price, stock, ran1, ran2]
    l.append(i)
    return l


def Remove(l, item): # deletes item(item) from inventory
    deleteI = BIsearch(l, 'des', item)
    if deleteI:
        print('Are you sure you want to delete', item)
        check = input('(y/n): ')
        if check.upper() == 'Y':
            l.remove(deleteI)
            return l
    else:
        return False


def posts(l):  # displays the list of items
    print('des |', 'price |', 'stock |', 'ran1 |', 'ran2')
    for i in l:
        print(i)
    print('')

def var_set(var):  #sets var to position in tuple
    if var == 'des':
        return 0
    if var == 'price':
        return 1
    if var == 'stock':
        return 2
    if var == 'ran1':
        return 3
    if var == 'ran2':
        return 4
    if var == 'value':  #sets var to trigger if statement for value
        return 5
    if var == 'all':   #sets var to trigger if statement for all
        return 6



def BBsort(l, var):   #bubble-sort a list(l) based on variable(var) input
    n = len(l)
    count = 0
    var1 = var_set(var)
    if var1 ==5:   #sorts by expected total value of the items(value)
        l1 = Val(l)
        for i in range(n - 1, 0, -1):
            swap = False
            count += 1
            for j in range(i):
                if l1[j] > l1[j + 1]:
                    l[j], l[j + 1] = l[j + 1], l[j]
                    l1[j], l1[j + 1] = l1[j + 1], l1[j]
                    swap = True
            if not swap:
                return l, count
        return l
    else:   #sorts by variable(var) input
        for i in range(n - 1, 0, -1):
            swap = False
            count += 1
            for j in range(i):
                if l[j][var1] > l[j + 1][var1]:
                    l[j], l[j + 1] = l[j + 1], l[j]
                    swap = True            
            if not swap:
                return l, count      
        return l


def Isort(l, var, blank = 0):   #insertion-sort a list(l) based on variable input(var)   
    n = len(l)
    var1 = var_set(var)
    if var1 == 5:  #sorts by expected total value of the items(value)
        l1 = Val(l)
        for i in range(1, n):
            value = l1[i]
            temp = l[i]
            pos = i
            while pos > 0 and value < l1[pos - 1]:
                l[pos] = l[pos-1]
                l1[pos] = l1[pos-1]
                pos -= 1
            l[pos] = temp
            l1[pos] = value
        return l
    elif var1 == 6:  #sorts for variable(all)
        for i in range(1, n):
            value = l[i][blank]
            temp = l[i]
            pos = i
            while pos > 0 and value < l[pos - 1][blank]:
                l[pos] = l[pos-1]
                pos -= 1
            l[pos] = temp
        return l
    else:    #sorts by variable(var) input
        for i in range(1, n):
            value = l[i][var1]
            temp = l[i]
            pos = i
            while pos > 0 and value < l[pos - 1][var1]:
                l[pos] = l[pos-1]
                pos -= 1
            l[pos] = temp
        return l

    

def BIsearch(l, var, target):    #binary-search a list(l) based on variable input(var) for a target value(target)  
    low = 0 
    high = len(l) - 1
    var1 = var_set(var)
    if var1 == 6:     #searchs the whole inventory for all instances of target(target)
        Alist = []
        target = str(target)
        for r in range(5):
            temp = Isort(l, var, r)
            for i in range(len(l)):
                check = True
                low = 0 
                high = len(l) - 1
                while check:
                    mid = round((low + high)/2)
                    if str(temp[mid][r]) == target:
                        Alist.append(l[mid])
                        temp.remove(l[mid])
                        check = False
                    elif str(l[mid][r]) > target:
                        high = mid - 1
                    else:
                        low = mid + 1
                    if high < low:
                        check = False
        for x in Alist:
            temp.append(x)
        return Alist
    elif var1 == 0: #des single result search
        temp = Isort(l, var)
        for i in range(len(l)):
            i = i
            check = True
            low = 0 
            high = len(l) - 1
            while check:
                mid = round((low + high)/2)
                if temp[mid][var1] == target:
                    return temp[mid]
                elif l[mid][var1] > target:
                    high = mid - 1
                else:
                    low = mid + 1
                if high < low:
                    return False
        return False
    else:   #searchs variable(var) for all instances of target(target)
        temp = Isort(l, var)
        tempL = []  
        for i in range(len(l)):
            i = i
            check = True
            low = 0 
            high = len(l) - 1
            while check:
                mid = round((low + high)/2)
                if temp[mid][var1] == target:
                    tempL.append(l[mid])
                    temp.remove(l[mid])
                    check = False
                elif l[mid][var1] > target:
                    high = mid - 1
                else:
                    low = mid + 1
                if high < low:
                    check = False
        for x in tempL:
            temp.append(x)
        return tempL
        


def Tstock(l):  #gives total stock of inventory
    total = 0
    for i in l:
        total += i[2]
    return total


def Astock(l):    #gives average stock of inventory
    t = Tstock(l)
    average = t/len(l)
    return average

def Val(l):  #value of items in inventory
    val = []
    for x in l:
        val.append(x[1]*x[2])
    return val


def Tval(l, n):   #Total value of inventory
    if n == 0:
        return l[0]
    return l[n] + Tval(l, n-1)


def checkD(d):  #checks for des duplicates
    check = BIsearch(inventory, 'des', d)
    if check:
        return False
    else:
        return True

def checkSt(l): #checks if any item in inventory is out of stock
    temp = BIsearch(l, 'stock', 0)
    if temp:
        for i in temp:
            print(i[0], 'is out of stock.')

def update(l, target, p, s, r1, r2): #updates item
    l = Isort(l, 'des')
    var1 = 0
    for i in range(len(l)):
        i = i
        check = True
        low = 0 
        high = len(l) - 1
        while check:
            mid = round((low + high)/2)
            if l[mid][var1] == target:
                l[mid] = [target, p, s, r1, r2]
                return l
            elif l[mid][var1] > target:
                high = mid - 1
            else:
                low = mid + 1
            if high < low:
                return False
    return False


inventory = []
des1 = ['apple', 'orange', 'pineapple', 'watermelon', 'pear', 'sneakers', 'table', 'chair', 'hanger', 'rope',
           'fan', 'computer', 'television', 'laptop', 'cabinet', 'cupboard', 'piano', 'guitar', 'stradivarius', 'triangle',
           'cow-bell', 'cymble', 'drum-set', 'tambourine', 'tuba', 'trombone', 'trumpet', 'french horn', 'clarinet', 'flute',
           'saxophone', 'banjo', 'viola', 'cello', 'ukulele', 'harp', 'double bass', 'toilet roll', 'katana', 'sai',
           'scythe', 'tea-bag', 'mace', 'claymore', 'ak-47', 'm4-a1', 'suitcase', 'rpg', 'airplane', 'trebuchet']
price1 = [1, 1, 3, 10, 1, 100, 70, 40, 1.20, 10,
         100, 2000, 300, 2000, 200, 150, 2500, 700, 16000000, 30,
         100, 100, 1500, 50, 600, 500, 400, 500, 300, 300,
         800, 120, 160, 500, 120, 800, 500, 10, 499, 139,
         699.99, 1.99, 76, 135, 900, 700, 130, 1000, 1000000, 1400]
stock1 = [10000, 10000, 5000, 5000, 10000, 100, 700, 700, 4000, 10000,
         1000, 2000, 2000, 2000, 700, 700, 20, 20, 2, 50, 
         40, 20, 20, 30, 40, 40, 40, 40, 40, 40,
         50, 20, 20, 20, 20, 20, 20, 100000, 100, 200,
         100, 0, 50, 50, 100, 100, 200, 10, 20, 40]
ran11 = ['red', 'orange', 'yellow', 'green', 'green', 'colourful', 'wood', 'wood', 'plastic', '5 meters',
        'standing', 'really good', '57 inch', 'really good', 'wood', 'wood', 'grand', 'classic', 'expensive', 'equalateral',
        'annoying', 'cymple', 'decked-out', 'brass', 'brass', 'brass', 'brass', 'brass', 'long', 'long',
        'brass', 'kazooie', 'beta violin', 'big violin', 'small guitar', 'opened piano', 'double the bass', '1 ply', 'sharp', 'stabby',
        'sow crop', 'while stocks lasts', 'heavy', 'big sword', 'rifle', 'rifle', 'bag', 'rocket launcher', 'can fly', 'wood']
ran21 = ['','','','','','','','','','',
        '','','','','','','','','','',
        '','','','','','','','','','',
        '','','','','','','','','','',
        '','','','','','','','','','']
for x in range(50):
    add(inventory, des1[x], price1[x], stock1[x], ran11[x], ran21[x])
while True:
    print('--------Choose Following--------\n'
          '1.Add to Inventory\n'
          '2.Remove from Inventory\n'
          '3.Display Inventory\n'
          '4.Update Item\n'
          '5.Quit')
    choice1 = input('Input Number: ')
    if choice1 == '1':   
        print('------------------------------')
        try:
            des = input('Input description/name of item: ')
            dupC = checkD(des)
            if not dupC:
                print('description already exists!')
                raise Exception
        except Exception:
            continue
        try:
            price = int(input('Input price of item: '))
        except Exception:
            print('Input should be a interger!')
            continue
        try:
            stock = int(input('Input stock of item: '))
        except Exception:
            print('Input should be a interger!')
            continue
        random1 = input('Input 1st random information of item: ')
        random2 = input('Input 2st random information of item: ')
        add(inventory, des, price, stock, random1, random2)
    elif choice1 == '2':
        print('------------------------------')
        delete = input('Input description/name of item to remove: ')
        try:
            trying = Remove(inventory, delete)
            if not trying:
                print('Item does not exist!')
                raise Exception
            else:
                print(delete, 'deleted!')
        except Exception:
            continue
    elif choice1 == '3':
        print('--------Choose Following--------\n'
              '1.View Inventory\n'
              '2.Sort Inventory\n'
              '3.Search Inventory\n'
              '4.Quit')
        choice2 = input('Input Number: ')
        if choice2 == '1':
            print('------------------------------')
            posts(inventory)
            print('Total Stock:', Tstock(inventory))
            print('Average Stock:', Astock(inventory))
            print('Total Value of all stock:', Tval(Val(inventory), len(inventory)-1))
            checkSt(inventory)
        elif choice2 == '2':
            print('------------------------------')
            SortInput = input('Sort by(des, price, stock, ran1, ran2, value): ')
            Isort(inventory, SortInput)
            posts(inventory)
        elif choice2 == '3':
            print('------------------------------')
            SearchInput = input('Search for: ')
            SearchVar = input('Search in(des, price, stock, ran1, ran2, all): ')
            print(BIsearch(inventory, SearchVar, SearchInput))
        else:
            break
    elif choice1 == '4':
        print('------------------------------')
        try:
            UpInput = input('Description of item to update: ')
            dupC = checkD(UpInput)
            if dupC:
                print('description does not exists!')
                raise Exception
        except Exception:
            continue
        try:
            price = int(input('Input price of item: '))
        except Exception:
            print('Input should be a interger!')
            continue
        try:
            stock = int(input('Input stock of item: '))
        except Exception:
            print('Input should be a interger!')
            continue
        random1 = input('Input 1st random information of item: ')
        random2 = input('Input 2st random information of item: ')
        update(inventory, UpInput, price, stock, random1, random2)
        print(UpInput, 'updated!')
    else:
        break
