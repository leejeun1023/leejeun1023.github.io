---
layout: post
title:  "Func.md"
date:   2018-10-16 16:09:13
categories: Data_science
permalink: /archivers/python_lecture_03
---
# Func.md
    x = 50
    def func(x):
        print 'x is', x
        x = 2
        print 'Changed local x to', x
    func(x)
    print 'x is still', x
    #1번 라인의 x와 2번 라인의 func(x)의 x는 다른 값
