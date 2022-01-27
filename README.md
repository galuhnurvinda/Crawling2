# Crawling2

    import pandas as pd
    from bs4 import BeautifulSoup
    import requests
    import csv
    #===========================================================================================================
    with open('Locations _ Hale and Hearty.html') as html_file:
    soup=BeautifulSoup(html_file, 'lxml')
    #============================================Lokasi=========================================================    
    semua1=soup.find_all("main" ,class_="main")
    for loc in semua1:
    cleansing_1= loc.find_all('h2', class_='sticky-list__title')
    #print(cleansing_1)
    for location in cleansing_1:
        print(location.text) #untuk cek variabel
    #==========================================Alamat============================================================        
    semua2=soup.find_all("main" ,class_="main")
    #print(semua)
    for loc in semua2:
    cleansing_2=loc.find_all('h3', class_='location-card__name')
    for address in cleansing_2:
        print(address.text)#untuk cek variabel
    #============================================Telpon==========================================================
    semua3=soup.find_all("main" ,class_="main")
    #print(semua)
    for loc in semua3:
    cleansing_3=loc.find_all('p', class_='location-card__phone')
    for phone in cleansing_3:
        print(phone.text.split()[-1])#untuk cek variabel
    #============================================Waktu Buka========================================================    
    semua4=soup.find_all("main" ,class_="main")
    #print(semua)
    for loc in semua4:    
    cleansing_4=loc.find_all('p', class_='location-card__hours-today')
    for time in cleansing_4:
        print(time.text)#untuk cek variabel
    #============================================Save tabel=======================================================        
    merge= {'Lokasi': ['Brooklyn','Long Island', 'Manhattan - Above 60th Street', 'Manhattan - Below 40th Street',
                       'Manhattan - Below 40th Street','Manhattan - Below 40th Street','Manhattan - Below 40th Street', 
                       'Manhattan - Below 40th Street','Manhattan - Below 40th Street','Manhattan - Below 40th Street',
                       'Manhattan - Between 40th & 59th','Manhattan - Between 40th & 59th','Manhattan - Between 40th & 59th',
                      'Manhattan - Between 40th & 59th','Manhattan - Between 40th & 59th','Manhattan - Between 40th & 59th',
                       'Manhattan - Between 40th & 59th'],
            'Alamat': ['MetroTech Center', 'Carle Place','64th & Lexington','Fulton Street','39th & Broadway',
                       '33rd & Madison','Hudson Street', '35th & 7th', 'Broad Street','Chelsea Market','40th & Madison',
                       'Rockefeller Plaza','40th & Lexington', '45th & Lexington','Grand Central Terminal', 
                       '56th & 6th','49th & 7th'],
            'No_Telpon': ["347-889-5258","516-535-1000","212-517-7600","646-454-0052","212-354-1199","646-692-8262","212-776-1780",
                         "212-971-0605","646-590-3588","212-255-2433","212-683-2222","212-265-2117","212-599-7220","646-580-1900",
                           "212-983-2845",
                         "212-245-9200", "212-221-9666"],
            'Waktu_Buka': ["Store Hours: 10:00 AM-5:00 PM","Store Hours: 10:00 AM-5:00 PM","Store Hours: 10:00 AM-8:00 PM",
                           "Store Hours: 10:00 AM-5:00 PM","Store Hours: 10:00 AM-5:00 PM","Store Hours: 10:00 AM-5:00 PM",
                            "Store Hours: 10:00 AM-5:00 PM","Store Hours: 10:00 AM-5:00 PM","Store Hours: 10:00 AM-5:00 PM",
                           "Store Hours: 10:00 AM-6:00 PM","Store Hours: 10:00 AM-5:00 PM","Store Hours: 10:00 AM-5:00 PM",
                           "Store Hours: 10:00 AM-5:00 PM","Store Hours: 10:00 AM-5:00 PM","Store Hours: 11:00 AM-6:00 PM",
                            "Store Hours: 10:00 AM-5:00 PM","Store Hours: 10:00 AM-5:00 PM"]}
   
    df = pd.DataFrame(data=merge)
    df
    df.to_csv('C:/Users/Bappenas/OneDrive/Pribadi/Narasi TV/scraping_final.csv', index=False) #folder path bisa disesuaikan
    
