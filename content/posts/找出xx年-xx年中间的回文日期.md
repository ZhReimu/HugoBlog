---
title: "找出一段时间内的回文日期"
description: "C语言回文日期"
tags: [ "C语言","函数调用","回文"]
categories: [ "C语言"]
keywords: [ "C语言"]
date: 2020-05-03T00:35:22Z
#lastmod:2020-1-1
# CJKLanguage: Chinese, Japanese, Korean
isCJKLanguage: true
# 如果draft为true，除非使用 --buildDrafts 参数，否则不会发布文章
draft: false
# 设置文章的过期时间，如果是已过期的文章则不会发布，除非使用 --buildExpired 参数
#expiryDate: 2020-01-01
# 设置文章的发布时间，如果是未来的时间则不会发布，除非使用 --buildFuture 参数
#publishDate: 2020-01-01
# 排序你的文章
#weight: 40
---

Talk is easy, Show you code！
```c
#include<stdio.h>
void separate(int a)
{
	int t = a, temp = 0;
	// 定义临时变量t存放输入的原始值,temp为逆序后的值
	while (t)
	{
		temp *= 10;
		temp += t % 10;
		t = t / 10;
	}
	// 当t不等于0时循环，依次取出各个位上的数字将其✖10后加到temp里
	// 达到逆序效果
	if (temp == a)
		printf("%d是回文数\n",a);
//	else
//		printf("不是回文数\n");
	// 如果逆序后的值等于逆序前的值那么它就是回文，否则不是

}

int GetDate(int MaxYear)
{
	int year = 1000, month = 1, day = 1, date, MaxDay;
	while (year <= MaxYear)
	{
		for (month = 1; month <= 12; month++)
		{
			date = year * 100 + month;
			if (month == 2)
			{
				date = year * 100;
				date += month;
				if (((year % 4 == 0) && (year % 100 != 0)) || year % 400 == 0)
					MaxDay = 29;
				else
					MaxDay = 28;
			}
			if (month == 1 || month == 3 || month == 5 || month == 7 || month == 8 || month == 10
				|| month == 12)
				MaxDay = 31;
			if (month == 3 || month == 4 || month == 6 || month == 9 || month == 11)
				MaxDay = 30;

			for (day = 1; day <= MaxDay; day++)
			{
				if (day < 10)
				{
					date *= 100;
					date += day;
				//	printf("%d\n", date);
				 separate(date);
					date /= 100;
				}
				else
				{
					date *= 100;
					date += day;
				//	printf("%d\n", date);
				 separate(date);
					date /= 100;
				}


			}
		}
		year++;

	}

}

void main()
{
	GetDate(2020);
	printf("程序结束\n");
}
```
