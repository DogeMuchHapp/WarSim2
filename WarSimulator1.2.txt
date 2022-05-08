import random

Cdeck = [2, 2, 3, 3, 4, 4, 5, 5, 6, 6, 7, 7, 8, 8, 9, 9, 10, 10,
         11, 11, 12, 12, 13, 13, 14, 14]
Mdeck = [2, 2, 3, 3, 4, 4, 5, 5, 6, 6, 7, 7, 8, 8, 9, 9, 10, 10,
         11, 11, 12, 12, 13, 13, 14, 14]

print("Windoge Software: War Simulator")
print("")


def give_to(player_from, player_to, index):
    player_to.append(player_from[index])
    player_from.pop(index)


def shuffle(tuple):
    tuple = list(tuple)
    random.shuffle(tuple)
    return tuple


def compare(index):
    global math
    print("Cdeck: " + str(len(Cdeck)))
    print("Mdeck: " + str(len(Mdeck)))
    print("Index: " + str(index))
    print("")
    if index > len(Cdeck) or index > len(Mdeck):
        math = 0
        return math
    if index < len(Cdeck) and index < len(Mdeck):
        if Cdeck[index] > Mdeck[index]:
            Cdeck.append(Mdeck[index])
            Mdeck.pop(index)
            Cdeck.append(Cdeck[index])
            Cdeck.pop(index)
        elif Mdeck[index] > Cdeck[index]:
            Mdeck.append(Cdeck[index])
            Cdeck.pop(index)
            Mdeck.append(Mdeck[index])
            Mdeck.pop(index)
        elif Cdeck[index] == Mdeck[index]:
            War(index)


def War(index):
    global takeL
    global Cdeck
    global Mdeck
    global math
    global maths
    fin_card = index + 4
    try:
        if Cdeck[fin_card] == Mdeck[fin_card]:
            try:
                Cdeck = shuffle(Cdeck)
                Mdeck = shuffle(Mdeck)
            except IndexError:
                if len(Cdeck) > len(Mdeck):
                    print("Cyan Wins! Magenta incapable of cards to play war")
                    print("Total Turns: " + str(maths))
                if len(Cdeck) > len(Mdeck):
                    print("Magenta Wins! Cyan incapable of cards to play war")
                    print("Total Turns: " + str(maths))
        if Cdeck[fin_card] > Mdeck[fin_card]:
            try:
                Cdeck.append(Mdeck[index + 1])
                Mdeck.pop(index + 1)
                Cdeck.append(Mdeck[index + 2])
                Mdeck.pop(index + 2)
                Cdeck.append(Mdeck[index + 3])
                Mdeck.pop(index + 3)
            except IndexError:
                if len(Cdeck) > len(Mdeck):
                    print("Cyan Wins! Magenta incapable of cards to play war")
                    print("Total Turns: " + str(maths))
        elif Mdeck[fin_card] > Cdeck[fin_card]:
            try:
                Mdeck.append(Cdeck[index + 1])
                Cdeck.pop(index + 1)
                Mdeck.append(Cdeck[index + 2])
                Cdeck.pop(index + 2)
                Mdeck.append(Cdeck[index + 3])
                Cdeck.pop(index + 3)
            except IndexError:
                if len(Cdeck) > len(Mdeck):
                    print("Magenta Wins! Cyan incapable of cards to play war")
                    print("Total Turns: " + str(maths))
    except IndexError:
        if len(Cdeck) > len(Mdeck):
            print("Cyan Wins! Magenta incapable of cards to play war")
            maths = maths + 1
            print("Total Turns: " + str(maths))
            takeL = False
        elif len(Mdeck) > len(Cdeck):
            print("Magenta Wins! Cyan incapable of cards to play war")
            maths = maths + 1
            print("Total Turns: " + str(maths))
            takeL = False


Cdeck = shuffle(Cdeck)
Mdeck = shuffle(Mdeck)

print("Cyan deck:")
print(Cdeck)
print("Magenta deck:")
print(Mdeck)

math = 0
maths = 0
takeL = True
while True:
    rushed_ui = input("Type 'Quit' or 'New'; 'Quit' to quit the program and 'New' to start a new game of war: ")
    if rushed_ui == 'New':
        Cdeck = [2, 2, 3, 3, 4, 4, 5, 5, 6, 6, 7, 7, 8, 8, 9, 9, 10, 10,
                 11, 11, 12, 12, 13, 13, 14, 14]
        Mdeck = [2, 2, 3, 3, 4, 4, 5, 5, 6, 6, 7, 7, 8, 8, 9, 9, 10, 10,
                 11, 11, 12, 12, 13, 13, 14, 14]
        Cdeck = shuffle(Cdeck)
        Mdeck = shuffle(Mdeck)
        takeL = True
        while takeL:
            if len(Cdeck) == 1 or len(Mdeck) == 1 and Cdeck[0] == Mdeck[0]:
                if len(Cdeck) > len(Mdeck):
                    try:
                        print("Cyan Wins, Magenta incapable of cards to play war!")
                    except IndexError:
                        pass
                elif len(Mdeck) > len(Cdeck):
                    try:
                        print("Magenta Wins, Cyan incapable of cards to play war!")
                    except IndexError:
                        pass
            compare(0)
            print(Cdeck)
            print(Mdeck)
            print("")
            math = math + 1
            if math >= len(Cdeck) or math >= len(Mdeck):
                math = 0
            maths = maths + 1
            if len(Cdeck) == 0:
                print("Magenta Wins, Cyan has zero cards!")
                print("Total Turns: " + str(maths))
                takeL = False
            if len(Mdeck) == 0:
                print("Cyan Wins, Magenta has zero cards!")
                print("Total Turns: " + str(maths))
                takeL = False
    elif rushed_ui == 'Quit':
        quit()
