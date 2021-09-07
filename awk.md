sed & awk
========



For command lines, the syntax is:
------------------------------------
    awk ’instructions’ files


using script file 
------------------

    awk -f scfl file 



variables 
---------

    $0     — while document 
    $1     — field one 
    $2    — field two
    ...
    ...


	awk regex 
	awk ‘/pattern/‘ file 


    awk '/line/' file                                     
    second line                                                          
    line three                                                           
    line four                                                            
    line five                                                            
    line six     



adding command to the awk 
------------------------------------
	
	
	iPad:~# awk '/line/' file                                     
	second line                                                          
	line three                                                           
	line four                                                            
	line five                                                            
	line six                                                             
	    
	
	Imrans-iPad:~# awk '/line/{print }' file                           
	line                                                                 
	three                                                               
	four                                                                 
	five                                                                 
	six                                                                  
	Imrans-iPad:~# 






changing field seperator 
------------------------------------

	Imrans-iPad:~# echo im/mm/jj | awk -F/ '/jj/{print $2}'              
	mm   



	multiple statements on data 
------------------------------------

	Imrans-iPad:~# echo '                                                
	
	> imran,nazir,parray                                                 
	> mubashir,mehraj,dar                                                
	> zubair,fayaz,mir' | awk -F, '{print ;print }'                  
	
	imran                                                                
	parray                                                               
	mubashir                                                           	
	dar                                                                  
	zubair                                                               
	mir            




combining sed and awk 
-------------------------


	Imrans-iPad:~# cat ff                                                
	l1 f1 f2 f3                                                          
	l2 f1 f2 f3                                                          
	l3 f1 f2 f3   

	Imrans-iPad:~# cat ff | sed -e 's/1/one/' -e 's/2/two/'              
	lone f1 ftwo f3                                                      
	ltwo fone f2 f3                                                      
	l3 fone ftwo f3                            
                          
	Imrans-iPad:~# cat ff | sed -e 's/1/one/' -e 's/2/two/' | awk '{print $2}'                                                                
	f1                                                                   
	fone                                                                 
	fone   
