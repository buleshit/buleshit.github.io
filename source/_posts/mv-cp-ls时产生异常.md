title: mv/cp/ls时产生异常
author: 有毒
tags:
  - cp
  - ls
  - mv
categories:
  - Linux命令
date: 2017-02-15 11:42:00
---
> * 使用ls或mv *命令时, 产生`"Arguments too long"或"Array list too long"`的错误信息
> * 使用cp时，产生`cp: will not overwrite just-created 'xxxx'`





解答：该错误的产生是由于/usr/include/sys/limits.h文件中ARG_MAX参数对应值的限制，最大值为24576，并且无法改变此限制。因此当某目录下的文件数超过24576时，可以使用下面的命令列示、删除或移动所有的文件：

1. 列示文件： 
`find <path> -name "*" | xargs ls -l `
2.  删除文件： 
`find . -name "*" |xargs rm {} `
3. 移动所有文件至目标目录：  
`find </sourcedirectory> -name "*" | xargs -I {} mv {}</destinationdir> `   
4.复制所有文件至目标目录：  
`find ${src_dir} -type f | xargs -i cp {} ${dst_dir}
`
