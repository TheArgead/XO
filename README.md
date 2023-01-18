# XO
Fist project in Github

print("""""""""""""")
print("             *             ")
print("            ***            ")
print("           *****           ")
print("          *******          ")
print("         *********         ")
print("        ***********        ")
print("       *************       ")
print("      ***************      ")
print("     *****************     ")
print("    *******************    ")
print("   *********************   ")
print("  ***********************  ")
print(" ************************* ")
print()
print("***************************")
print("* Добро пожаловать в игру *")
print("*""*""*""*"" 'Крестики нолики' ""*""*""*""*")
print("*""*""*""*""*"" Игра начинается ""*""*""*""*""*")
print("***************************")
print("")

bord = list(range(1, 10))

wins_coord = [(1, 2, 3), (4, 5, 6), (7, 8, 9), (1, 4, 7), (2, 5, 8), (3, 6, 9), (1, 5, 9), (3, 5, 7)]


def draw_board():
    print("-------------")
    for i in range(3):
        print("|", bord[0 + i * 3], "|", bord[1 + i * 3], "|", bord[2 + i * 3], "|")
    print("-------------")


def take_input(player_token):
    while True:
        value = input("Выберите область, куда поставить " + player_token + "? ")
        if not (value in "123456789"):
            print("Неверное обозначение. Введите повторно.")
            continue
        value = int(value)
        if str(bord[value - 1]) in "XO":
            print("Клетка занята, выберите другую")
            continue
        bord[value - 1] = player_token
        break


def check_win():
    for each in wins_coord:
        if (bord[each[0] - 1]) == (bord[each[1] - 1]) == (bord[each[2] - 1]):
            return bord[each[1] - 1]
    else:
        return False


def main():
    counter = 0
    while True:
        draw_board()
        if counter % 2 == 0:
            take_input("X")
        else:
            take_input("O")
        if counter > 3:
            winner = check_win()
            if winner:
                draw_board()
                print(winner, "Вы одержали победу !")
                break
        counter += 1
        if counter > 8:
            draw_board()
            print("Ничья !")
            break


main()
