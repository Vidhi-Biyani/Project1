# load in the webdriver gem to interect with selenium
require 'selenium-webdriver'
#setup chrome plugin
driver = Selenium::WebDriver::Chrome.driver_path='C:\Users\vidhi\Desktop\Ruby Folder\chromedriver.exe'
#this line will start the browser
driver = Selenium::WebDriver.for :chrome
#Navigate to URl
driver.get "http://www.google.com"
#Maximize the window
driver.manage.window.maximize
#find locator of google search
searchbox=driver.find_element(:name,"q")
#Enter text in google search
searchbox.send_keys("selenium tutorial")
#Locator of Google search
searchbox=driver.find_element(:name,"btnK")
driver.action.send_keys(:shift).perform
driver.action.send_keys(:return).perform
#Find Elements of all links that is common
results=driver.find_elements(:css,".r>a")
results.each do |results|
  #click links
  results.click
  #Verify title of first link
  puts "Page title is: #{driver.title}"
  #wait for 8 sec
  sleep 8
  #Click on back
  driver.navigate.back
  #driver.manage.timeouts.page_load = 120
end
