# 111
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from selenium.webdriver.common.keys import Keys
import time

# 配置ChromeDriver
driver_path = '/path/to/chromedriver'  # 替换为你的chromedriver路径
driver = webdriver.Chrome(executable_path=driver_path)

# 打开Melon Ticket 国际版网站
driver.get("https://www.tkglobal.melon.com/main/index.hetm?langCd=EN")

# 登录
def login(username, password):
    driver.find_element(By.ID, "loginId").send_keys(username)
    driver.find_element(By.ID, "loginPwd").send_keys(password)
    driver.find_element(By.ID, "loginButton").click()

# 进入抢票页面
def go_to_ticket_page():
    # 假设你已经有票的链接，可以直接进入
    driver.get("https://tkglobal.melon.com/performance/index.htm?langCd=EN&prodld=210230")

# 抢票逻辑
def try_to_buy_ticket():
    while True:
        try:
            # 这里假设有一个按钮的ID为 "buyNow"，点击它
            buy_button = driver.find_element(By.ID, "buyNow")
            buy_button.click()
            print("成功点击抢票按钮!")
            break
        except Exception as e:
            print("按钮未加载，刷新页面重试...")
            driver.refresh()
            time.sleep(0.5)  # 可以调节频率，但太频繁可能会被识别为Bot

# 用户登录信息
username = "vulnerablyevader@gmail.com"
password = "nichkhun52"

login(username, password)
go_to_ticket_page()
try_to_buy_ticket()

# 保持浏览器打开，或者根据需要关闭
time.sleep(10)  # 等待足够时间后再关闭
driver.quit()
