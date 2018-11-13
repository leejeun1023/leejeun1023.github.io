---
layout: post
title:  "자판기 만들기"
date:   2018-11-13 16:09:13
categories: Data_science
permalink: /archivers/python_lecture_07
---
# vending_machine_solution.md 
    # 물건 수급 - 판매중 상태에서 관리자 모드를 활성화 시키는 코드를 입력하면 문이 열린다.
    # 관리자 모드 - 관리자는 물품을 선택하고 해당 물품의 숫자를 보충할 수 있다. 
    # 여기에서 10개가 넘으면 저장공간이 꽉 찼다는 메세지를 보낸다. 
    # 물건을 고르고, 물건을 골랐을 때, 
    # 비용이 적절하면 물건과 함께 거스름돈이 나온다.
    # 비용이 모자라면 금액을 더 입력해달라는 메세지가 나온다. 
    # 물건이 떨어지면 [매진] 메시지를 출력하시오.

    vending_condition = True

    admin_code = 1023

    total_money = 0 

    item1_name = "Coke"
    item1_price = 1000
    item1_num = 5

    item2_name = "Soda"
    item2_price = 1000
    item2_num = 1

    item3_name = "Coffee"
    item3_price = 500
    item3_num = 4

    item4_name = "Tea"
    item4_price = 400
    item4_num = 8

    item5_name = "Chocolate"
    item5_price = 1000
    item5_num = 2

    item6_name = "Gum"
    item6_price = 500
    item6_num = 9

    while vending_condition:
        #재고 체크
        if item1_num == 0 and item2_num == 0 and item3_num == 0 and item4_num == 0 and item5_num == 0 and item6_num == 0:
            print "All sold out"
            print "Change: {}".format(total_money)
            total_money = 0
            break
        else:
            print "Tatal money: {0}".format(total_money) 
            # hidden code = 5928
            print "[1.{}: {} / 2.{}: {} /  3.{}: {} / 4.{}: {} / 5.{}: {} / 6.{}: {} / 7. Insert coin / 8. Return coin /            9.Exit]".format(item1_name, item1_num, item2_name, item2_num, item3_name, item3_num, item4_name, item4_num, item5_name, item5_num, item6_name, item6_num)
            vending_machine_mode = int(raw_input("Select mode: "))
            print "========"
    
            if vending_machine_mode == admin_code:
                admin_condition = True
                while admin_condition:
                    print "! Admin mode !"
                    print "[1.{}: {} 2.{}: {} 3.{}: {} 4.{}: {} 5.{}: {} 6.{}: {} 0. Exit]".format(item1_name, item1_num, item2_name, item2_num, item3_name, item3_num, item4_name, item4_num, item5_name, item5_num, item6_name, item6_num)
                    print "Fillng stock" 
                    adding_item_id = int(raw_input("Item id: "))
                
                    if adding_item_id == 0:
                        admin_condition = False
                        continue
                    else:
                        print "How many do you want to fill?" 
                        adding_item_ea = int(raw_input("Item ea: "))
                        if adding_item_id == 1:
                            if item1_num+adding_item_ea <=10:
                                item1_num += adding_item_ea
                                print "Added {}: {}".format(item1_name, adding_item_ea)
                            else:
                                print "{}: Maximum".format(item1_name)
                                return_item_ea = adding_item_ea + item1_num -10
                                item1_num = 10
                                print "Returned {}: {}".format(item1_name, return_item_ea)
                            
                        elif adding_item_id == 2:
                            if item2_num+adding_item_ea <=10:
                                item2_num += adding_item_ea
                                print "Added {}: {}".format(item2_name, adding_item_ea)
                            else:
                                print "{}: Maximum".format(item2_name)
                                return_item_ea = adding_item_ea + item2_num -10
                                item1_num = 10
                                print "Returned {}: {}".format(item2_name, return_item_ea)
                            
                        elif adding_item_id == 3:
                            if item3_num+adding_item_ea <=10:
                                item3_num += adding_item_ea
                                print "Added {}: {}".format(item3_name, adding_item_ea)
                            else:
                                print "{}: Maximum".format(item3_name)
                                return_item_ea = adding_item_ea + item1_num -10
                                item3_num = 10
                                print "Returned {}: {}".format(item3_name, return_item_ea)
                            
                        elif adding_item_id == 4:
                            if item4_num+adding_item_ea <=10:
                                item4_num += adding_item_ea
                                print "Added {}: {}".format(item4_name, adding_item_ea)
                        else:
                            print "{}: Maximum".format(item4_name)
                            return_item_ea = adding_item_ea + item1_num -10
                            item4_num = 10
                            print "Returned {}: {}".format(item4_name, return_item_ea)
                            
                        elif adding_item_id == 5:
                            if item5_num+adding_item_ea <=10:
                                item5_num += adding_item_ea
                                print "Added {}: {}".format(item5_name, adding_item_ea)
                            else:
                                print "{}: Maximum".format(item5_name)
                                return_item_ea = adding_item_ea + item5_num -10
                                item5_num = 10
                                print "Returned {}: {}".format(item5_name, return_item_ea)
                            
                        elif adding_item_id == 6:
                            if item6_num+adding_item_ea <=10:
                                item6_num += adding_item_ea
                                print "Added {}: {}".format(item6_name, adding_item_ea)
                            else:
                                print "{}: Maximum".format(item6_name)
                                return_item_ea = adding_item_ea + item6_num -10
                                ite6_num = 10
                                print "Returned {}: {}".format(item6_name, return_item_ea)
                        else:
                            print "! Error !"
            
            elif vending_machine_mode == 1:
                if item1_num != 0:
                    if item1_price <= total_money:
                        print "{}".format(item1_name)
                        total_money -= item1_price
                        item1_num -= 1
                    else:
                        print "Please insert more coins."
                else:
                    print "Sold out."
            elif vending_machine_mode == 2:
                if item2_num != 0:
                    if item2_price <= total_money:
                        print "{}".format(item2_name)
                        total_money -= item2_price
                        item2_num -= 1
                    else:
                        print "Please insert more coins."
                else:
                    print "Sold out."
            elif vending_machine_mode == 3:
                if item3_num != 0:
                    if item3_price <= total_money:
                        print "{}".format(item3_name)
                        total_money -= item3_price
                        item3_num -= 1
                    else:
                        print "Please insert more coins."
                else:
                    print "Sold out."
            elif vending_machine_mode == 4:
                if item4_num != 0:
                    if item4_price <= total_money:
                        print "{}".format(item4_name)
                        total_money -= item4_price
                        item4_num -= 1
                    else:
                        print "Please insert more coins."
                else:
                    print "Sold out."
            elif vending_machine_mode == 5:
                if item5_num != 0:
                    if item5_price <= total_money:
                        print "{}".format(item5_name)
                        total_money -= item5_price
                        item5_num -= 1
                    else:
                        print "Please insert more coins."
                else:
                    print "Sold out."
            elif vending_machine_mode == 6:
                if item6_num != 0:
                    if item6_price <= total_money:
                        print "{}".format(item6_name)
                        total_money -= item6_price
                        item6_num -= 1
                    else:
                        print "Please insert more coins."
                else:
                    print "Sold out."
            elif vending_machine_mode == 7:
                # 물건 판매 - 소비자는 금액을 입력
                inserted_money = int(raw_input("Insert coin: "))
                total_money += inserted_money
                print "Total coin: {0}".format(inserted_money)
        
            elif vending_machine_mode == 8:
                # 반환 버튼을 누르면 현재 금액을 반환
                print "Change: {0}".format(total_money)
                total_money = 0
            else: 
                # wrong number
                print "! Error !" 
    else: 
        print u"We are out of stock and close our business."
