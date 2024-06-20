
1、MySQL-python：只支持python2 是对C语言操作数据库的一个简单封装     
2、mysqlclient：是1的分支效率最高，安装时容易因环境经常出现各种问题        
3、pymysql：纯pthon实现效率不如2，但是无缝衔接python    
4、mysql-connector-python：MySQL官方退出，效率慢  
-- pip install pymysql  
不直接使用原生sql语句进行操作 使用ORM方式操作 Flask-SQLAlchemy操作   
-- pip install flask-sqlalchemy 
可以合并数据库不使用# with app.app_context():db.create_all() 相当于能动态更新数据库表     
-- pip install flask-migrate        
from flask_migrate import Migrate       
migrate = Migrate(app,db)   
**ORM模型映射成表的三步**    
**1.flask db init #只需要执行一次**    
**2.flask db migrate #每次添加模型类后执行 识别ORM模型的改变，生成迁移脚本**    
**3.flask db upgrade #执行迁移脚本，完成ORM模型和数据库的映射,运行迁移脚本，同步到数据库中**    

```python
from flask import Flask,request,render_template
from flask_sqlalchemy import SQLAlchemy
from sqlalchemy import text
from datetime import datetime

app = Flask(__name__)

#MySQL所在的主机名
HOSTNAME = '127.0.0.1'
#MySQL监听的端口号，默认3306
PORT = 3306
#数据库的账号
USERNAME = 'root'
#数据库密码
PASSWORD = 'root'
#数据库名称
DATABASE = 'database_learn'

app.config['SQLALCHEMY_DATABASE_URI'] = f"mysql+pymysql://{USERNAME}:{PASSWORD}@{HOSTNAME}:{PORT}/{DATABASE}?charset=utf8mb4"

db = SQLAlchemy(app)
with app.app_context():
    with db.engine.connect() as conn:
        rs = conn.execute(text("SELECT 1"))
        print(rs.fetchone()) #(1,)
```