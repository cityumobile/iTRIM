TRIM in system idle time (iTRIM)
==================================

Written by Yu Liang <yliang22-c@my.cityu.edu.hk>

To comprehensively describe the impact of TRIM on I/O performance of mobile devices
We propose a novel TRIM framework for F2FS to improve both short-term and long-term performance.
To figure out the influence of TRIM on I/O performance, we compare the latencies of real operations on mobile devices when TRIM is on and when TRIM is off. 
Both shortterm and long-term performance are considered in our experiments. 
To improve short-term performance, we design a novel iTRIM framework to conduct TRIM in system idle time. 
To conquer the challenge of the uncertainty in idle time duration, an effective solution is designed. 

-------------------------------------------
Details of implementation
1. segment.c  add my_clear_prefree_segments() for five functions:
	1) Search pre-free section map to find a set of continuos sections as TRIM unit for TRIM
    2) Clear the flag for prefree map.
    3) Degrade the number of prefree sections
	4) set respoding segno as free
	5)TRIM the TRIM unit
2. gc.c  if idle to call add my_clear_prefree_segments()
3. cp.c drop the function related to discard.

Download HuaweiP9 source code from
-----------------------------------
    http://consumer.huawei.com/en/opensource/detail/?siteCode=worldwide&keywords=p9&fileType=openSourceSoftware&pageSize=10&curPage=1


Change the kernel 
------------------------
	using our kernel
 
Complie and build boot.img
--------------
	according to the instruction of huaweiP9
	
Flash boot.img to your mobile device



2018-2-8, Yu Liang <yliang22-c@my.cityu.edu.hk>


