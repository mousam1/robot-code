from tkinter import*
import random


###declaring different variables that will be used throughout the code
moveSpeed = 35                 
backHeight = 500             
backWidth =  600             
backDisplay = Tk() #nyama kakvo da se promeni 
backDisplay.minsize(width = backWidth, height = backHeight)    
backDisplay.maxsize(width = backWidth, height = backHeight)  
objectX1 = random.randint(20,300) 
objectY1 = random.randint(20,300)
objectX2 = objectX1 + 25         
objectY2 = objectY1 - 25         
gameCanvas = Canvas(backDisplay, bg='grey', width = backWidth,height = backHeight) 


gameCanvas.pack()    
rectOne = gameCanvas.create_rectangle(50, 50, 30, 30, fill='grey')                   
rectTwo= gameCanvas.create_rectangle(objectX1, objectY1, objectX2, objectY2, fill='black') 






#Comands for movement of the rectangle:




def keyUp(play):


    global objectX1, objectY1, objectY2, objectX2
    cx1, cy1, cx2, cy2 = gameCanvas.coords(rectOne)


    if cy1 <= 15:
        gameCanvas.coords(rectOne, cx1, cy1, cx2, cy2)
    else:
        if cy1 > (objectY1 - 30) and cy1 < (objectY1 + 30) and cx1 > objectX1 and cx1 < objectX2:
            if gameCanvas.itemcget(rectTwo, "fill") == 'grey':
                gameCanvas.itemconfig(rectTwo, fill='black')
            elif gameCanvas.itemcget(rectTwo, "fill") == 'black':
                objectX1 = random.randint(30, 250)
                objectY1 = random.randint(30, 250)
                objectX2 = objectX1 + 25
                objectY2 = objectY1 - 25
                gameCanvas.coords(rectTwo, objectX1, objectY1, objectX2, objectY2)
        elif cy1 > (objectY1 - 30) and cy1 < (objectY1 + 30) and cx2 > objectX1 and cx2 < objectX2:
            if gameCanvas.itemcget(rectTwo, "fill") == 'grey':
                gameCanvas.itemconfig(rectTwo, fill = 'black')
            elif gameCanvas.itemcget(rectTwo, "fill") == 'black':
                objectX1 = random.randint(30, 250)
                objectY1 = random.randint(30, 250)
                objectX2 = objectX1+25
                objectY2 = objectY1-25
                gameCanvas.coords(rectTwo,objectX1, objectY1, objectX2, objectY2)
        gameCanvas.coords(rectOne, cx1, cy1 - moveSpeed, cx2, cy2 - moveSpeed)






        
def keyLeft(play):


    global objectX1, objectY1, objectY2, objectX2
    cx1, cy1, cx2, cy2 = gameCanvas.coords(rectOne)


    if cx1 <= 15:
        gameCanvas.coords(rectOne, cx1, cy1, cx2, cy2)
    else:
        if cx1 < (objectX2 + 30) and cx1 > (objectX2 - 30) and cy1 < objectY1 and cy1 > objectY2:
            if gameCanvas.itemcget(rectTwo, "fill") == 'grey':
                gameCanvas.itemconfig(rectTwo, fill='black')
            elif gameCanvas.itemcget(rectTwo, "fill") == 'black':
                objectX1 = random.randint(20, 300)
                objectY1 = random.randint(20, 300)
                objectX2 = objectX1+25
                objectY2 = objectY1-25
                gameCanvas.coords(rectTwo, objectX1, objectY1, objectX2, objectY2)
        elif cx1 < (objectX2 + 30) and cx1 > (objectX2 - 30) and cy2 < objectY1 and cy2 > objectY2:
            if gameCanvas.itemcget(rectTwo, "fill") == 'grey':
                gameCanvas.itemconfig(rectTwo, fill='black')
            elif gameCanvas.itemcget(rectTwo, "fill") == 'black':
                objectX1 = random.randint(20, 300)
                objectY1 = random.randint(20, 300)
                objectX2 = objectX1 + 25
                objectY2 = objectY1 - 25
                gameCanvas.coords(rectTwo, objectX1, objectY1, objectX2, objectY2)
        gameCanvas.coords(rectOne, cx1 - moveSpeed, cy1, cx2 - moveSpeed, cy2)










def keyRight(play): #V     Funkciq koqto se izpulnqva kogato natisnesh dqsnata strelka 


    global objectX1, objectY1, objectY2, objectX2 #Deklarirash global variables / ble-ta
    cx1, cy1, cx2, cy2 = gameCanvas.coords(rectOne) #Dava ti koordinatite na rectOne, sirech purviq pravougulnik, cx1=lqva strana, cx2=dqsna strana, cy1=gorna strana, cy2=mnogo dolna strana


    if cx2 >= backWidth - 15: 
        gameCanvas.coords(rectOne, cx1, cy1, cx2, cy2)
    else:
        if cx2 > (objectX1 - 30) and cx2 < (objectX1 + 30) and cy1 < objectY1 and cy1 > objectY2:
            if gameCanvas.itemcget(rectTwo, "fill") == 'grey':
                gameCanvas.itemconfig(rectTwo, fill='black')
            elif gameCanvas.itemcget(rectTwo, "fill") == 'black':
                objectX1=random.randint(20, 300)
                objectY1=random.randint(20, 300)
                objectX2=objectX1 + 25
                objectY2=objectY1 - 25
                gameCanvas.coords(rectTwo, objectX1, objectY1, objectX2, objectY2)
        elif cx2 > (objectX1 - 30) and cx2 < (objectX1 + 30) and cy2 < objectY1 and cy2 > objectY2:       
            if gameCanvas.itemcget(rectTwo, "fill") == 'grey':
                gameCanvas.itemconfig(rectTwo, fill='black')
            elif gameCanvas.itemcget(rectTwo, "fill") == 'black':
                objectX1 = random.randint(20,300)
                objectY1 = random.randint(20,300)
                objectX2 = objectX1 + 25
                objectY2 = objectY1 - 25
                gameCanvas.coords(rectTwo, objectX1, objectY1, objectX2, objectY2)
        gameCanvas.coords(rectOne, cx1 + moveSpeed, cy1, cx2 + moveSpeed, cy2)   


        




def keyDown(play):


    global objectX1, objectY1, objectY2, objectX2
    cx1, cy1, cx2, cy2 = gameCanvas.coords(rectOne)


    if cy2 >= backHeight - 15:
        gameCanvas.coords(rectOne, cx1, cy1, cx2, cy2)
    else:
        if cy2 > (objectY2 - 30) and cy2 < (objectY2 + 30) and cx1 > objectX1 and cx1 < objectX2:
            if gameCanvas.itemcget(rectTwo, "fill") == 'grey':
                gameCanvas.itemconfig(rectTwo, fill='black')
            elif gameCanvas.itemcget(rectTwo, "fill") == 'black':
                objectX1 = random.randint(30,250)
                objectY1 = random.randint(30,250)
                objectX2 = objectX1 + 25
                objectY2 = objectY1 - 25
                gameCanvas.coords(rectTwo, objectX1, objectY1, objectX2, objectY2)
        elif cy2 > (objectY2 - 30) and cy2 < (objectY2 + 30) and cx2 > objectX1 and cx2 < objectX2:
            if gameCanvas.itemcget(rectTwo, "fill") == 'grey':
                gameCanvas.itemconfig(rectTwo, fill='black')
            elif gameCanvas.itemcget(rectTwo, "fill") == 'black':
                objectX1 = random.randint(30,250)
                objectX2 = objectX1 + 25
                objectY2 = objectY1 - 25
                gameCanvas.coords(rectTwo, objectX1, objectY1, objectX2, objectY2)
        gameCanvas.coords(rectOne, cx1, cy1 + moveSpeed, cx2, cy2 + moveSpeed)


gameCanvas.update()                  
gameCanvas.bind('<Right>', keyRight) 
gameCanvas.bind('<Left>', keyLeft)    
gameCanvas.bind('<Up>', keyUp)      
gameCanvas.bind('<Down>', keyDown)  
gameCanvas.focus_set()              
backDisplay.mainloop()

