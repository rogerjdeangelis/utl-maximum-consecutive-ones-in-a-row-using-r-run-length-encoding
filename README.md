# utl-maximum-consecutive-ones-in-a-row-using-r-run-length-encoding
Maximum consecutive ones in a row using r run length encoding    
    Maximum consecutive ones in a row using r run length encoding                                                                      
                                                                                                                                       
    githgub                                                                                                                            
    https://tinyurl.com/y5skr2ff                                                                                                       
    https://github.com/rogerjdeangelis/utl-maximum-consecutive-ones-in-a-row-using-r-run-length-encoding                               
                                                                                                                                       
    SAS Forum (Realted to)                                                                                                             
    Add across row till non-1                                                                                                          
    https://tinyurl.com/y4bca3sc                                                                                                       
    https://communities.sas.com/t5/SAS-Programming/Add-across-row-till-non-1/m-p/670112                                                
    Related to but not the same as posted. It seems to me that any row that begins with a missing should have 0 '1s'                   
                                                                                                                                       
    /*                   _                                                                                                             
    (_)_ __  _ __  _   _| |_                                                                                                           
    | | `_ \| `_ \| | | | __|                                                                                                          
    | | | | | |_) | |_| | |_                                                                                                           
    |_|_| |_| .__/ \__,_|\__|                                                                                                          
            |_|                                                                                                                        
    */                                                                                                                                 
                                                                                                                                       
    options validvarname=upcase;                                                                                                       
    libname sd1 "d:/sd1";                                                                                                              
    data sd1.have(keep=y: );;                                                                                                          
    input ID$ y y1 y2 y3 y4 y5 y6 y7 y8 y9 y10 ;                                                                                       
    cards4;                                                                                                                            
    A 1 1 1 . . . 1 1 . . .                                                                                                            
    B . . . 1 1 1 . . . . 1                                                                                                            
    C . . . . . . . . . . .                                                                                                            
    D . 1 1 1 1 1 1 1 1 . .                                                                                                            
    E . . . . . . . . . . .                                                                                                            
    F 1 1 . 1 . . 1 1 . . .                                                                                                            
    G . . . . . 1 1 1 1 . 1                                                                                                            
    H . . . . . . . . . . 1                                                                                                            
    I . 1 1 1 . . . . . . .                                                                                                            
    G 1 . . . . . . . 1 . .                                                                                                            
    K 1 1 1 1 1 . . . . . .                                                                                                            
    ;;;;                                                                                                                               
    run;quit;                                                                                                                          
                                                                                                                                       
                                                                                                                                       
     SD1.HAVE total obs=11                                             | RULES                                                         
                                                                      |                                                                
     ID   Y    Y1    Y2    Y3    Y4    Y5    Y6    Y7    Y8    Y9    Y10  | XaxRunLength                                               
                                                                          |                                                            
     A    1     1     1     .     .     .     1     1     .     .     .   |   3   Y,Y1,Y2                                              
     B    .     .     .     1     1     1     .     .     .     .     1   |   3   Y3,Y4,Y5                                             
     C    .     .     .     .     .     .     .     .     .     .     .   |   0   No conceutive 1s                                     
     D    .     1     1     1     1     1     1     1     1     .     .   |   8                                                        
     E    .     .     .     .     .     .     .     .     .     .     .   |   0                                                        
     F    1     1     .     1     .     .     1     1     .     .     .   |   2                                                        
     G    .     .     .     .     .     1     1     1     1     .     1   |   4                                                        
     H    .     .     .     .     .     .     .     .     .     .     1   |   1                                                        
     ID   .     1     1     1     .     .     .     .     .     .     .   |   3                                                        
     G    1     .     .     .     .     .     .     .     1     .     .   |   1                                                        
     K    1     1     1     1     1     .     .     .     .     .     .   |   5  First 5                                               
                                                                       |                                                               
                                                                                                                                       
    /*           _               _                                                                                                     
      ___  _   _| |_ _ __  _   _| |_                                                                                                   
     / _ \| | | | __| `_ \| | | | __|                                                                                                  
    | (_) | |_| | |_| |_) | |_| | |_                                                                                                   
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                                                  
                    |_|                                                                                                                
    */                                                                                                                                 
                                                                                                                                       
                                                                                                                                       
    WORK.WANT total obs=11                                                                                                             
                                                                                                                                       
       ID    MAXLEN                                                                                                                    
                                                                                                                                       
       A        3                                                                                                                      
       B        3                                                                                                                      
       C        0                                                                                                                      
       D        8                                                                                                                      
       E        0                                                                                                                      
       F        2                                                                                                                      
       G        4                                                                                                                      
       H        1                                                                                                                      
       ID       3                                                                                                                      
       G        1                                                                                                                      
       K        5                                                                                                                      
                                                                                                                                       
    /*                                                                                                                                 
     _ __  _ __ ___   ___ ___  ___ ___                                                                                                 
    | `_ \| `__/ _ \ / __/ _ \/ __/ __|                                                                                                
    | |_) | | | (_) | (_|  __/\__ \__ \                                                                                                
    | .__/|_|  \___/ \___\___||___/___/                                                                                                
    |_|                                                                                                                                
    */                                                                                                                                 
                                                                                                                                       
                                                                                                                                       
    options validvarname=upcase;                                                                                                       
    libname sd1 "d:/sd1";                                                                                                              
    data sd1.have(keep=y: );;                                                                                                          
    input ID$ y y1 y2 y3 y4 y5 y6 y7 y8 y9 y10 ;                                                                                       
    cards4;                                                                                                                            
    A 1 1 1 . . . 1 1 . . .                                                                                                            
    B . . . 1 1 1 . . . . 1                                                                                                            
    C . . . . . . . . . . .                                                                                                            
    D . 1 1 1 1 1 1 1 1 . .                                                                                                            
    E . . . . . . . . . . .                                                                                                            
    F 1 1 . 1 . . 1 1 . . .                                                                                                            
    G . . . . . 1 1 1 1 . 1                                                                                                            
    H . . . . . . . . . . 1                                                                                                            
    I . 1 1 1 . . . . . . .                                                                                                            
    G 1 . . . . . . . 1 . .                                                                                                            
    K 1 1 1 1 1 . . . . . .                                                                                                            
    ;;;;                                                                                                                               
    run;quit;                                                                                                                          
                                                                                                                                       
                                                                                                                                       
    %utlfkil(d/xpt/want.xpt);                                                                                                          
                                                                                                                                       
    proc datasets lib=work nolist;                                                                                                     
     delete wantxpt want;                                                                                                              
    run;quit;                                                                                                                          
                                                                                                                                       
    %utl_submit_r64(resolve('                                                                                                          
    library(haven);                                                                                                                    
    library(SASxport);                                                                                                                 
    have <- as.data.frame(read_sas("d:/sd1/have.sas7bdat"));                                                                           
    /* replace missings with 0 - nice */                                                                                               
    have[is.na(have)] <- 0;                                                                                                            
    /* max seq of 1s using rle run length encoding */                                                                                  
    want<-as.data.frame(apply(have, 1, function(x) {                                                                                   
      r <- rle(x);                                                                                                                     
      max(r$lengths[as.logical(r$values)]);                                                                                            
    }));                                                                                                                               
    colnames(want)<-"maxlen";                                                                                                          
    write.xport(want,file="d:/xpt/want.xpt");                                                                                          
    '));                                                                                                                               
                                                                                                                                       
    libname xpt xport "d:/xpt/want.xpt";                                                                                               
    data wantxpt;                                                                                                                      
      set xpt.want;                                                                                                                    
    run;quit;                                                                                                                          
    libname xpt clear;                                                                                                                 
                                                                                                                                       
    data want;                                                                                                                         
      merge have(keep=id)  wantxpt;                                                                                                    
    run;quit;                                                                                                                          
                                                                                                                                       
                                                                                                                                       
