def solution(n, s, t):
    hit_and_sunk = 0
    hit_not_sunk = 0
    not_hit = 0

    # S is empty
    if not s:
        return '{},{}'.format(hit_and_sunk, hit_not_sunk)

    # T is empty
    if not t:
        return '{},{}'.format(hit_and_sunk, hit_not_sunk)

    s_index = 0
    s_cordinates = {}
    s_square_count = []

    for ship in s.split(','):
        top_left, bottom_right = ship.split(' ')

        top_left_cordinate = (int(top_left[0:-1]) - 1, ord(top_left[-1]) - ord('A'))
        bottom_right_cordinate = (int(bottom_right[0:-1]) - 1, ord(bottom_right[-1]) - ord('A'))

        s_square_count.append((bottom_right_cordinate[0] - top_left_cordinate[0] + 1) * (bottom_right_cordinate[1] - top_left_cordinate[1] + 1))

        for row in range(top_left_cordinate[0], bottom_right_cordinate[0] + 1):
            for column in range(top_left_cordinate[1], bottom_right_cordinate[1] + 1):
                s_cordinates[(row, column)] = s_index

        s_index += 1

    print('Ship area {}'.format(s_square_count))
    print('Ship cordinates {}'.format(s_cordinates))

    s_square_count_copy = s_square_count.copy()

    for hit in t.split(' '):
        hit_cordinate = (int(hit[0:-1]) - 1, ord(hit[-1]) - ord('A'))

        print('Hit {}'.format(hit_cordinate))

        if hit_cordinate in s_cordinates:
            ship_index = s_cordinates[hit_cordinate]
            s_square_count_copy[ship_index] -= 1

    print('Remaining {}'.format(s_square_count_copy))

    for index in range(len(s_square_count_copy)):
        if s_square_count_copy[index] == s_square_count[index]:
            not_hit += 1
            # Ship hasn't been hit yet
            continue

        if s_square_count_copy[index] == 0:
            # Ship has been sunk
            hit_and_sunk += 1
        elif s_square_count_copy[index] > 0 and s_square_count_copy[index] < s_square_count[index]:
            # Ship has been hit but not yet sunk
            hit_not_sunk += 1

    return '{},{}'.format(hit_and_sunk, hit_not_sunk)


print(solution(4, '1B 2C,2D 4D', ''))
print('-------------------')
print(solution(4, '1B 2C,2D 4D', '2B 2D 3D 4D 4A'))
print('-------------------')
print(solution(3, '1A 1B,2C 2C', '1B'))
print('-------------------')
print(solution(12, '1A 2A,12A 12A', '12A'))
