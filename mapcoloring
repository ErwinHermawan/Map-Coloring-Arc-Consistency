clr = []
constraints = []
city = []

#cities = int(input("Enter number of states: "))
while True:
    cities = (input("Enter number of Cities: "))
    try:
        cities = int(cities)
    except:
        print('Please use number.')
        continue
    if cities < 1:
        print('Please enter a positive number.')
        continue
    break

for i in range(cities):
    con = []
    lis = input("Enter cities: ")
    k = int(input("Enter number of neighbor: "))
    for a in range(k):
        listconstraints = input("Enter neighbor: ")
        con.append(listconstraints)
    city.append(lis)
    constraints.append(con)


while True:
    clrs = int(input("Enter number of colors: "))
    try:
        clrs = int(clrs)
    except:
        print('Please use number.')
        continue
    if clrs < 1:
        print('Please enter a positive number.')
        continue
    break
for i in range(cities):
    colors = []
    for a in range(clrs):
        color = input("Enter color: ")
        colors.append(color)
    clr.append(colors)

assignments = { }
arcs = []

def ArcConsistency():

    #fill queue with arc consistency
    fillQueue()

    #check if arcs is empty
    while arcs:
        #get an object in dictionary and remove it from queue by using pop to remove the specified index from the list
        arcVars = arcs.pop(0)
        if revise(arcVars[0], arcVars[1]):

            dIIndex = city.index(arcVars[0])
            #checking if we have no more color in Di
            if len(clr[dIIndex]) == 0:
                print ("No more color")
                return False

            #add neighbors
            neighbors = list(constraints[dIIndex])
            neighbors.remove(arcVars[1])

            for ok in neighbors:
                arcs.append([ok, arcVars[0]])

    print (assignments)
    return True


#fill queue with initial arcs
def fillQueue():

    for var in city:

        varIndex = city.index(var)
        for arc in constraints[varIndex]:
            arcs.append([var, arc])

def revise( Xi, Xj):
    revised = False

    Iindex = city.index(Xi);

    
    #for each value in the domain
    for x in clr[Iindex]:

        #check if city is adjacent, if not, go to next x
        if Xj not in constraints[Iindex]:
            break

        if Xj not in assignments:
            continue

        #if adjacent city has current assignment of X (same color)
        if x in assignments[Xj]:
            clr[Iindex].remove(x)  #remove x from Di
            revised = True


    if not revised and len(clr[Iindex]) > 0:
        assignments[Xi] = clr[Iindex][0]

    return revised
ArcConsistency()
