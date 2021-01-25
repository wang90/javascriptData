## 利用dateime查找当天数据
``````
import datetime
from dateutil import parser

def getTimeDomain( hours = 1):
    nowdate = datetime.datetime.utcnow()
    now_time = nowdate.strftime('%Y-%m-%d')
    tomorrow_time = (nowdate + datetime.timedelta( hours = 24 * hours )).strftime('%Y-%m-%d')
    startStr = now_time + 'T00:00:01Z'
    endStr = tomorrow_time + 'T00:00:01Z'
    starttime = parser.parse(startStr)
    endtime = parser.parse(endStr)
    days = [ starttime, endtime ]
    return days
    
# mongo 查询部分
days = getTimeDomain()
query = {
    "uid" : uid,
    "created_at":{
      "$gte":  days[0],
      "$lt" : days[1],
    }
}
``````
