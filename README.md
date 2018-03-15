# GDUF-QZAPI
广东金融学院强智教务系统API

根据智校园APP抓包得出，兼容可使用智校园APP的其它学校的教务系统。\
除authUser API外，记得带上登录态。
## 提示
由于条件限制，部分参数作用仍未明晰，欢迎fork帮助我们改进。

公告和留言功能API尚未整理。
## API列表
### authUser
登录帐号\
<code>http://jwxt.gduf.edu.cn/app.do?method=authUser&xh=#学号#&pwd=#密码#</code>

**返回值**
> flag：未知\
userrealname：真实姓名\
token：令牌\
userdwmc：学院名称\
usertype：用户类别\
msg：登录状态

### getStudentIdInfo
获取学号信息\
<code>http://jwxt.gduf.edu.cn/app.do?method=getStudentIdInfo&xh=#学号#</code>

**返回值**
> bjid：未知\
ndzyid：未知\
yxid：未知\
xxdm：未知

### getCurrentTime
获取当前时间、周次、学年等信息\
<code>http://jwxt.gduf.edu.cn/app.do?method=getCurrentTime&currDate=#查询日期#</code>

**返回值**
> zc：未知\
e_time：本周结束日期\
s_time：本周起始日期\
xnxqh：学年

### getKbcxAzc
获取课程表\
<code>http://jwxt.gduf.edu.cn/app.do?method=getKbcxAzc&xh=#学号#&xnxqid=#学年#&zc=#未知，与getCurrentTime返回的zc相同#</code>

**返回值**\
返回JSON数组
> jsmc：课程教室\
jssj：下课时间\
jsxm：教师姓名\
kcmc：课程名称\
jcsj：未知，可能是课程ID\
kkzc：课程教学周\
kssj：上课时间\
sjbz：未知

### getKxJscx
获取空教室\
<code>http://jwxt.gduf.edu.cn/app.do?method=getKxJscx&time=#查询日期#&idleTime=#见下方说明#</code>

**idleTime取值**
> allday：全天\
am：上午\
pm：下午\
night：晚上

**返回值**\
返回JSON数组
> jsh：教室ID\
jsid：教室ID（与jsh相同）\
jsmc：教室名称\
jzwid：所在楼ID\
jzwmc：所在楼名\
xqmc：校区\
yxzws：教室容量\
zws：未知，和yxzws相同

### getXqcx
获取校区\
<code>http://jwxt.gduf.edu.cn/app.do?method=getXqcx</code>

**返回值**\
返回JSON数组
> xqid：校区ID\
xqmc：校区名称

### getJxlcx
获取校区教学楼信息\
<code>http://jwxt.gduf.edu.cn/app.do?method=getJxlcx&xqid=#校区ID#</code>

**返回值**\
返回JSON数组
> jzwid：教学楼教学楼ID\
jzwmc：教学楼名称

### getKxJscx
精确查询空教室\

<code>http://jwxt.gduf.edu.cn/app.do?method=getKxJscx&time=#查询日期#&idleTime=#见getKxJscx#&xqid=#校区ID#&jxlid=#教学楼ID#&classroomNumber=_#可容纳人数，见下方说明#</code>
xqid、jxlid、classroomNumber是可选参数
**classroomNumber**
> 30：30人以下\
30-40：30-40人\
40-50：40-50人\
60：60人以上
**返回值**\
返回JSON数组
> jsh：教室ID\
jsid：教室ID（与jsh相同）\
jsmc：教室名称\
jzwid：所在楼ID\
jzwmc：所在楼名\
xqmc：校区\
yxzws：教室容量\
zws：未知，和yxzws相同

### getUserInfo
获取帐号信息\
<code>http://jwxt.gduf.edu.cn/app.do?method=getUserInfo&xh=#学号#</code>

**返回值**\
> bj：班级\
dh：电话号码\
dqszj：未知\
email：电子邮箱\
fxzy：辅修专业\
ksh：高考考号\
nj：年级\
qq：QQ号\
rxnf：入学年份\
usertype：用户类别\
xb：性别\
xh：学号\
xm：姓名\
xz：未知\
yxmc：院系名称\
zymc：专业名称

### getXnxq
获取学年和学期信息\
<code>http://jwxt.gduf.edu.cn/app.do?method=getXnxq&xh=#学号#</code>

**返回值**\
返回JSON数组
> isdqxq：未知\
xnxq01id=学期学年ID\
xqmc：学期名称

### getCjcx
获取成绩信息\
<code>http://jwxt.gduf.edu.cn/app.do?method=getCjcx&xh=#学号#&xnxqid=#学期学年ID#</code>

**返回值**\
条件所限，尚未明晰

### getKscx
获取考试信息\
<code>http://jwxt.gduf.edu.cn/app.do?method=getKscx&xh=#学号#</code>

**返回值**\
条件所限，尚未明晰

### getEarlyWarnInfo
获取学籍预警信息\
<code>http://jwxt.gduf.edu.cn/app.do?method=getEarlyWarnInfo&xh=#学号#&history=#见下方说明#</code>

**history取值**
> 0：当前预警\
1：历史预警

**返回值**\
条件所限，尚未明晰
