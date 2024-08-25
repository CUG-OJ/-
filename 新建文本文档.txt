# If you cannot see Chinese, please use UTF-8 or GBK encoding to open this file.
USE CUGOJ;
CREATE TABLE users (
#     user_id INTEGER(11) NOT NULL AUTO_INCREMENT PRIMARY KEY,    # 用户ID(唯一)
    username VARCHAR(48) NOT NULL UNIQUE,                       # 用户名(唯一)
    password VARCHAR(32) NOT NULL,                              # 密码
    email VARCHAR(100) NOT NULL,                                # 邮箱
    reg_time DATETIME NOT NULL,                                 # 注册时间
    captain_id INTEGER(11),                                     # 队长ID
    token TEXT,                                                 # 当前设备
    school VARCHAR(32),                                         # 学校
    faculty VARCHAR(32)                                         # 院系
);
create table teams (
    user_id INTEGER(11) NOT NULL,                               # 队长ID
    team_name VARCHAR(48),                                      # 队伍名
    member_id_1 INTEGER(11),                                    # 队员2
    member_id_2 INTEGER(11),                                    # 队员3
    reg_time DATETIME NOT NULL                                  # 注册时间
);
create table class(
    class_id INTEGER(11) NOT NULL AUTO_INCREMENT PRIMARY KEY,   # 班级ID(唯一)
    class_name VARCHAR(48) NOT NULL,                            # 班级名
    teacher_id INTEGER(11) NOT NULL,                            # 教师(群主)ID
    reg_time DATETIME NOT NULL                                  # 注册时间
);
CREATE TABLE news (
    news_id INTEGER(11) NOT NULL AUTO_INCREMENT PRIMARY KEY,    # 新闻ID(唯一)
    user_id INTEGER(11) NOT NULL,                               # 发布者ID
    time DATETIME NOT NULL,                                     # 发布时间
    title VARCHAR(255) NOT NULL,                                # 标题
    content TEXT NOT NULL,                                      # 内容
    picture_url VARCHAR(255)                                    # 图片链接
);
CREATE TABLE problem(
    problem_id INTEGER(11) NOT NULL AUTO_INCREMENT PRIMARY KEY, # 题目ID(唯一)
    title VARCHAR(255) NOT NULL,                                # 题目标题
    user_id INTEGER(11) NOT NULL,                               # 发布者ID
    time_limit INTEGER(11) NOT NULL,                            # 时间限制
    memory_limit INTEGER(11) NOT NULL,                          # 内存限制
    description TEXT NOT NULL,                                  # 题目描述
    input TEXT NOT NULL,                                        # 输入描述
    output TEXT NOT NULL,                                       # 输出描述
    sample_input TEXT NOT NULL,                                 # 样例输入
    sample_output TEXT NOT NULL,                                # 样例输出
    hint TEXT,                                                  # 提示
    source VARCHAR(255)                                         # 来源
);
CREATE TABLE solution(
    solution_id INTEGER(11) NOT NULL AUTO_INCREMENT PRIMARY KEY,# 提交ID(唯一)
    problem_id INTEGER(11) NOT NULL,                            # 题目ID
    user_id INTEGER(11) NOT NULL,                               # 提交者ID
    time DATETIME NOT NULL,                                     # 提交时间
    language INTEGER(11) NOT NULL,                              # 编程语言
    code TEXT NOT NULL,                                         # 代码
    result INTEGER(11) NOT NULL,                                # 结果
    time_used INTEGER(11),                                      # 运行时长(ms)
    memory_used INTEGER(11)                                     # 内存
);
CREATE TABLE similarity(
    similarity_id INTEGER(11) NOT NULL AUTO_INCREMENT PRIMARY KEY,# 相似度ID(唯一)
    solution_id INTEGER(11) NOT NULL,                           # 提交ID
    similarity FLOAT(11) NOT NULL                               # 相似度
);
CREATE TABLE contest (
    contest_id INTEGER(11) NOT NULL AUTO_INCREMENT PRIMARY KEY, # 比赛ID(唯一)
    title VARCHAR(255) NOT NULL,                                # 竞赛标题
    user_id INTEGER(11) NOT NULL,                               # 发布者ID
    start_time DATETIME NOT NULL,                               # 开始时间
    end_time DATETIME NOT NULL,                                 # 结束时间
    password VARCHAR(32),                                       # 密码(可选)
    language_mask BIGINT(64) NOT NULL                           # 编程语言(多选)
);
CREATE TABLE contest_problem(
    contest_id INTEGER(11) NOT NULL,                            # 比赛ID
    problem_id INTEGER(11) NOT NULL,                            # 题目ID
    count_accepted INTEGER(11) NOT NULL,                        # 通过数
    count_submitted INTEGER(11) NOT NULL                        # 提交数
);
CREATE TABLE online_users (
    user_id INTEGER(11) NOT NULL,                               # 用户ID
    ip VARCHAR(15) NOT NULL,                                    # IP地址
    time DATETIME NOT NULL                                      # 开始时间
);