# Coding-Club-Task
import requests
import csv
response=requests.get('http://api.football-data.org/v2/competitions/',headers={'X-Auth-Token':'7190a0c62406430c9786cc45fb4780c5'})
tier = input('Enter the tier')
data = response.json()
ourdata = []
csvheader = ['id','name','area','available seasons','tier']
for i in range(156):
    if data['competitions'][i]['plan'] == tier:
        id = f"{data['competitions'][i]['id'],data['competitions'][i]['name'],data['competitions'][i]['numberOfAvailableSeasons'],data['competitions'][i]['plan']}"

        ourdata.append(id)

        with open('football.csv','w',encoding='UTF8',newline='') as f:
              writer = csv.writer(f)

              writer.writerow(csvheader)
              writer.writerows(ourdata)
