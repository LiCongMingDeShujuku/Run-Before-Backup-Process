![CLEVER DATA GIT REPO](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/0-clever-data-github.png "李聪明的数据库")

# 在备份过程之前运行
#### Run Before Backup Process
**发布-日期: 2015年06月17日 (评论)**

![#](images/##############?raw=true "#")

## Contents

- [中文](#中文)
- [English](#English)
- [SQL Logic](#Logic)
- [Build Info](#Build-Info)
- [Author](#Author)
- [License](#License) 


## 中文
每当你通过代理作业实现自动备份流程时，最好在运行你现有的非常有用的备份流程之前，确保你已在sys.configuration中进行了适当的设置。这就是我总是在整个备份过程之前设置以下配置的原因。


## English
It’s generally a good idea whenever you have automated backup processes through  to make sure you have the proper settings in sys.configurations before running the ever so helpful backup process you have in place. This is why I always set the following configurations just before the overall backup process beings.

---
## Logic
```SQL
use master;
set nocount on
declare @sqlversion varchar(25)
set 	@sqlversion = (select substring (@@version, 21, 5))
if 		@sqlversion > 2005
	begin
		exec master..sp_configure ‘show advanced options’, 		‘1’ reconfigure;
		exec master..sp_configure ‘backup compression default’, ‘1’ reconfigure;
		exec master..sp_configure ‘agent xps’, 					‘1’ reconfigure;
		exec master..sp_configure ‘xp_cmdshell’, 				‘1’ reconfigure;
	end
	else
		exec master..sp_configure ‘agent xps’, 					‘1’ reconfigure;
		exec master..sp_configure ‘xp_cmdshell’, 				‘1’ reconfigure;


```



[![WorksEveryTime](https://forthebadge.com/images/badges/60-percent-of-the-time-works-every-time.svg)](https://shitday.de/)

## Build-Info

| Build Quality | Build History |
|--|--|
|<table><tr><td>[![Build-Status](https://ci.appveyor.com/api/projects/status/pjxh5g91jpbh7t84?svg?style=flat-square)](#)</td></tr><tr><td>[![Coverage](https://coveralls.io/repos/github/tygerbytes/ResourceFitness/badge.svg?style=flat-square)](#)</td></tr><tr><td>[![Nuget](https://img.shields.io/nuget/v/TW.Resfit.Core.svg?style=flat-square)](#)</td></tr></table>|<table><tr><td>[![Build history](https://buildstats.info/appveyor/chart/tygerbytes/resourcefitness)](#)</td></tr></table>|

## Author

- **李聪明的数据库 Lee's Clever Data**
- **Mike的数据库宝典 Mikes Database Collection**
- **李聪明的数据库** "Lee Songming"

[![Gist](https://img.shields.io/badge/Gist-李聪明的数据库-<COLOR>.svg)](https://gist.github.com/congmingshuju)
[![Twitter](https://img.shields.io/badge/Twitter-mike的数据库宝典-<COLOR>.svg)](https://twitter.com/mikesdatawork?lang=en)
[![Wordpress](https://img.shields.io/badge/Wordpress-mike的数据库宝典-<COLOR>.svg)](https://mikesdatawork.wordpress.com/)

---
## License
[![LicenseCCSA](https://img.shields.io/badge/License-CreativeCommonsSA-<COLOR>.svg)](https://creativecommons.org/share-your-work/licensing-types-examples/)

![Lee Songming](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/1-clever-data-github.png "李聪明的数据库")

