# Developing Zblog application on pagoda server

by : 百度

**note : ** this document refereing to zblog documentation page [here](https://docs.zblogcn.com/php/#/ "here"), if there any miss configure and or any step not working properly please read the documentation for an answer.

## Zblog instalation

### Manual method
- clone zblog application from github page
`
git clone https://github.com/zblogcn/zblogphp.git zblog_dir
`

- setup domain for pointing to zblog instalation folder `zblog_dir`

- setup pseudo static and point root url to pointing root folder (inside the `zblog_dir/`)

```
// pagoda default pseudo static for zblog
if (-f $request_filename/index.html){
	rewrite (.*) $1/index.html break;
}
if (-f $request_filename/index.php){
	rewrite (.*) $1/index.php;
}
if (!-f $request_filename){
	rewrite (.*) /index.php;
}

```
- access domain with domain / IP registered then continue instalation guide from documentation.

<mark >
Note: sometimes clone directly from github can end up with error thema not found because source code on github didn't provide any theme. installing it over internet can causing installation not finish.
</mark>  

### Automatic method

- makesure we already have domain.
- then add it to pagoda choose `一键部署` on top panel pop up window then select zblog
- follow instrucsion, and magic happen

### Migration method
- compress all web files inside the zblog application
- export database useb by xblog application
- move to another domain directory extract all web files to the `/` of directory
- import exported database
- set pseudo static conffiguration

```
// pagoda default pseudo static for zblog
if (-f $request_filename/index.html){
	rewrite (.*) $1/index.html break;
}
if (-f $request_filename/index.php){
	rewrite (.*) $1/index.php;
}
if (!-f $request_filename){
	rewrite (.*) /index.php;
}

```
- and magic happen, done


## Template instalation
### File Upload Method
For template instalation via File Upload we must have theme file provided by Zblog Application Centre. Some of creator inside the Zblog Applicatin Center provide free theme which can be download and install to our zblog site.
- download tempelate from [Zblog Application Center](https://app.zblogcn.com/?cate=4 "Zblog Application Center")
- result of downloaded file is .zba file. upload it on `your_domain.com/zb_system/admin/index.php?act=PluginMng`
- activate theme and theme installed to your sistem. to make any modification or configuration just click manage icon on theme box

### Application Centre Method
If you have premium template, or you bought a premium template usually can't be download, so to install it to your sistem you must install it from Zblog Application Center.
- Login to Zblog application center and click `进入后台` button enter dashboard mode.
- choose `生成令牌` to enter token generator page
- click `生成` button to generate token and keep the key
- go to admin page pf ypur application, on sidebar menu, choose `应用中心` menu.
- on Application Center page click `登录应用商城` on top menu
- enter your key and and login.
- in Application center top menu choose `我的应用仓库`
- select template then click `获取应用`
- go to tempelate configuration page then activate template. Done.

### End
