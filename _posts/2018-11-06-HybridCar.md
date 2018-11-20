---
layout: post
title:  "HybridCar"
date:   2018-11-06 17:25:13
categories: Data_science
permalink: /archivers/python_lecture_08
---
# 하이브리드 
    #가솔린 자동차
    def class Car:
        def __init__(self, model_name):
            self.model_name = model_name
        def stop(self):
            print "Engine stop"   
        def start_and_speed_up(self):
            print "Engine run"
        def fixed_speed(self):
            print "Drive"   
        def speed_down(self):
            print "Break"
        def get_model_name(self):
            print self.model_name + "is driving."

    # 전기 자동차        
    def class ElectricCar:
        def __init__(self, model_name):
            self.model_name = model_name  
        def stop(self):
            print "Motor stop"
        def start_and_speed_up(self):
            print "Motor run"
        def fixed_speed(self):
            print "Drive."
        def speed_down(self):
            print "Break and Battery charge"
        def get_model_name(self):
            print self.model_name + "is driving."
        
    # 하이브리드 자동차     
    def class HybridCar(Car,ElectricCar):
        def __init__(self, model_name):
            self.model_name = model_name
            Car.stop(self)
            ElectricCar.stop(self)
            Car.start_and_speed_up(self)
            ElectricCar.start_and_speed_up(self)
            Car.fixed_speed(self)
            ElectricCar.fixed_speed(self)
            Car.speed_down(self)
            ElectricCar.speed_down(self)  
        def get_model_name(self):
            print self.model_name + "is driving."

    def main():
        print "메인함수 입니다."
        car_1 = Car("GasolineCar_1")  
        car_1.get_model_name()
        car_1.stop()
        car_1.start_and_speed_up()
        car_1.fixed_speed()
        car_1.speed_down()

    if __name__ == '__main__':
        main()
