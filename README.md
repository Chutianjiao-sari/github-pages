import sympy as sp

# 定义符号变量
n, i = sp.symbols('n i')  # i 作为求和变量
h = 100  # 初始高度
g = 9.8  # 重力加速度

# 计算第n次反弹的反弹高度的符号表达式
rebound_height_expr = h / (2**n)

# 计算总路程的符号表达式
total_distance_expr = h + 2 * sp.summation(h / (2**i), (i, 1, n-1)) + rebound_height_expr

# 计算总时间的符号表达式
fall_time_expr = sp.sqrt(2 * h / g)  # 自由落体时间公式
total_time_expr = fall_time_expr + 2 * sp.summation(sp.sqrt(2 * (h / (2**i)) / g), (i, 1, n-1)) + sp.sqrt(2 * rebound_height_expr / g)


# 计算并输出第10次掉下并反弹到最高点时的具体结果
n_val = 10  # 第10次反弹
rebound_10 = rebound_height_expr.subs(n, n_val).evalf()  # 转换为浮点数
total_distance_10 = total_distance_expr.subs(n, n_val).evalf()  # 转换为浮点数
total_time_10 = total_time_expr.subs(n, n_val).evalf()  # 转换为浮点数

# 输出结果
print(f"\n第10次掉下并反弹到最高点时：")
print(f"反弹高度为 {rebound_10:.2f} 米")
print(f"此时球一共经过的路程为 {total_distance_10:.2f} 米")
print(f"此时球的运动时间为 {total_time_10:.2f} 秒")

# 输出符号表达式
print(f"第n次反弹高度的符号表达式：H_n = {rebound_height_expr}")
print(f"总路程的符号表达式：D_n = {total_distance_expr}")
print(f"总时间的符号表达式：T_n = {total_time_expr}")
