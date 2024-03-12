```mysql
set names utf8mb4; -- 占据更多的存储空间，但是显示特殊符号
int(11) -- 显示宽度为11，不影响int空间
varchar(48) -- 变长存储，更节省空间，但速度慢
mediumtext -- 可以存储2^24-1个字符
tinyint(4) -- 大小 1 byte
smallint(6) -- [-2^15,2^15–1]2个byte
varbinary(60) -- 变长，最多60个字节
defunct -- 僵尸进程
DECIMAL(10,3) -- 总位数最多10位，小数点3位
collate utf8mb4_unicode_ci -- 排序方式
datetme -- '1000-01-01 00:00:00.000000' to '9999-12-31 23:59:59.999999'
timestamp -- '1970-01-01 00:00:01.000000' to '2038-01-19 03:14:07.999999'
```
```mermaid
erDiagram
    compileinfo{
        int(11) solution_id(PRIMARY_KEY)
        text error
    }
    
    contest{
        int(11) contest_id(PRIMARY_KEY)
        varchar(255) title
        datetime start_time
        datetime end_time
        %%僵尸进程
        char(1) defunct 
        text description
        tinyint(4)  private
        %%bits for LANG to mask1
        int langmask
        CHAR(16) password
        varchar(48) user_id
    }
    contest_problem{
    	int(11) problem_id
    	int(11) contest_id(Index_contest_id)
    	title char(200)
    	int(11) num
    	int(11) c_accepted
    	int(11) c_submit
    }
    loginlog{
    	varchar(48) user_id(user_log_index)
    	varchar(40) password(user_log_index)
    	varchar(46) ip
    	datetime time
    }
    
```

```mermaid
erDiagram 
    mail{
    	skip skip
    }
    news{
    	int(11) news_id
    	varchar(48) user_id
    	varchar(200) title
    	mediumtext content
    	datetime time
    	tinyint(4) importance
    	int(11) menu
    	char(1) defunct
    }
    privilege{
        char(48) user_id
        char(30) rightstr
        char(11) valuestr
        char(1) defunct
    }
    problem{
    	int(11) problem_id(PRIMARY_KEY)
    	varchar(200) title
    	mediumtext description
    	mediumtext input
    	mediumtext output
    	text sample_input
    	text sample_output
    	char(1) spj
    	text hint
    	varchar(100) source
    	datetime in_date
    	DECIMAL(10_3) time_limit
    	int(11) memory_limit
    	char(1) defunct
    	int(11) accepted
    	int(11) submit
    	int(11) solved
    	varchar(16) remote_oj
    	varchar(32) remote_id
    }
```

```mermaid
erDiagram
	reply{
		int(11) rid(PRIMARYKEY)
		varchar(48) author_id(author_id)
		datetime time
		text content
		int(11) topic_id
		int(2) status
		varchar(46) ip
	}
	sim{
		int(11) s_id(PRIMARYKEY)
		int(11) sim_s_id
		int(11) sim
	}
	solution{
		int(11) solution_id
		int(11) problem_id
		char(48) user_id
		char(20) nick
		int(11) time
		int(11) memory
		datetime in_date
		smallint(6) result
	}
	source_code{
		int(11) solution_id
		text source
	}
```

```mermaid
erDiagram
	topic{
		int(11) tid(PRIMARYKEY)
		varbinary(60) title
		int(2) status
		int(2) top_level
		int(11) cid(cid)
		int(11) pid(cid)
		varchar(48) author_id
	}
	users{
		varchar(48) user_id(PRIMARYKEY)
		varchar(100) email
		int(11) submit
		int(11) solved
		char(1) defunct
		varchar(46) ip
		datetime accesstime
		int(11) volume
		int(11) language
		varchar(32) password
		datetime reg_time
		varchar(20) nick
		varchar(20) school
		varchar(16) group_name
		varchar(16) activecode
	}
	online{
		varchar(32) hash(PRIMARY_KEY__UNIQUE_KEY)
		varchar(46) ip
		varchar(255) ua
		varchar(255) refer
		int(10) lastmove
		int(10) firsttime
		varchar(255) uri
	}
	runtimeinfo{
		int(11) solution_id(PRIMARY_KEY)
		text error
	}
```

```mermaid
erDiagram
	printer{
		int(11) printer_id(PRIMARY_KEY)
		char(48) user_id
		datetime in_date
		smallint(6) status
		timestamp worktime
		CHAR(16) printer
		text content
	}
	balloon{
		int(11) balloon_id(PRIMARY_KEY)
		char(48) user_id
		int(11) sid
		int(11) cid
		int(11) pid
		smallint(6) status
	}
	share_code{
		int(11) share_id(PRIMARY_KEY)
		varchar(48) user_id
		varchar(32) title
		text share_code
		varchar(32) language
		datetime share_time
	}
```

