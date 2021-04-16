def coin_change(coin_list, change):
    min_num = change
    if change in coin_list:
        return 1
    else:
        for i in [for coin in coin_list if coin < change]:
            temp_num = 1 + coin_change(coin_list, change - i)
            if temp_num < min_num:
                min_num = temp_num
    return min_num


def coin_change(coin_list, change, change_record):
    min_num = change
    if change in coin_list:
        change_record[change] = 1
        return 1
    elif change_record[change] > 0:
        return change_record[change]
    else:
        for i in [for coin in coin_list if coin < change]:
            temp_num = 1 + coin_change(coin_list, change - i)
            if temp_num < min_num:
                min_num = temp_num
                change_record[change] = min_num
    return min_num

def dp_coin_change(coin_list, change, min_coins):
    for cent in range(change + 1):
        coin_count = cent
        for j in [c for c in coin_list if c <= cent]:
            if min_coins[cent - j] + 1 < coin_count:
                coin_count = min_coins[cent - j] + 1
        min_coins[cent] = coin_count
    return min_coins[change]

def dp_coin_change(coin_list, change, min_coins, coin_used):
    for cent in range(change + 1):
        coin_count = cent
        new_count = 1
        for j in [c for c in coin_list if c < cent]:
            if min_coins[cent - j] + 1 < coin_count:
                coin_count = min_coins[cent - j] + 1
                new_count = j
        min_coins[cent] = coin_count
        coin_used[cent] = j
    return min_coins[change]

def print_coin(coin_used, change):
    coin = change
    while coin > 0:
        this_coin = coin_used[coin]
        print_coin(this_coin)
        coin = coin - this_coin

def main():
    amnt = 63
    clist = [1, 5, 10, 21, 25]
    coin_used = [0] * (amnt + 1)
    coin_count = [0] * (amnt + 1)
    print("Making change for ", amnt, "requires")
    print(dp_coin_change(clist, amnt, coin_count, coin_used), "coins")
    print("They are:")
    print_coin(coin_used, amnt)
    print("The used list ia as follows:")
    print(coin_used)

main()
