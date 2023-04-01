import os
from selenium import webdriver
import random

classes = ["Barbarian", "Bard", "Cleric", "Druid", "Fighter", "Monk", "Paladin", "Ranger", "Rogue", "Sorcerer", "Warlock", "Wizard", "Artificer", "Bloodhunter"]
races = ['Aarakocra', 'Fallen Aasimar', 'Protector Aasimar', 'Scourge Aasimar', 'Bugbear', 'Centaur', 'Changeling',
'Dragonborn', 'Grey Dwarf', 'Hill Dwarf', 'Mountain Dwarf', 'Drow', 'Eladrin Elf', 'High Elf', 'Sea Elf',
'Shadar-Kai Elf', 'Wood Elf', 'Firbolg', 'Air Genasi', 'Earth Genasi', 'Fire Genasi', 'Water Genasi',
'Githyanki', 'Githzerai', 'Deep Gnome', 'Forest Gnome', 'Rock Gnome', 'Goblin', 'Goliath', 'Half Elf',
'Half Orc', 'Ghostwise Halfling', 'Lightfoot Halfling', 'Stout Halfling', 'Hobgoblin', 'Human',
'Kalashtar', 'Kenku', 'Kobold', 'Leonin', 'Lizardfolk', 'Loxodon', 'Minotaur', 'Orc', 'Satyr', 'Beasthide Shifter',
'Longtooth Shifter', 'Swiftstride Shifter', 'Simic Hybrid', 'Tabaxi', 'Tiefling', 'Feral Tiefling',
'Tortle', 'Vedalken', 'Verdan', 'Warforged', 'Yuan-ti Pureblood', 'Fairy'] 

genders = ["Male", "Female", "Non-Binary"]

def getRace():
    race = ""
    print("Please select your character's race, if you wish to have this randomly selected, type 'Random'")
    race = input("Race:").title()

    while race not in races:
        if race == "Random":
            race = random.choice(races)
        else:
             print("Please select a valid race")
             return getRace()
    return race


def getGender():
    gender = ""
    print("Please select your character's gender, if you wish to have this randomly selected, type 'Random'")
    gender = input("Gender:").title()

    while gender not in genders:
        if gender == "Random":
            gender = random.choice(genders)
        else:
            print("Please select a valid gender")
            return getGender()
    return gender


def getName(race, gender):

    malenames = []
    femalenames = []
    nonbinarynames = []
    name = ""

    while name == "":
        print("Please select your character name, if you wish to randomly select a name type 'Random'")
        name = input("Name:").title()
        if name != "Random": 
            return name

    if race in ['Hill Dwarf', 'Mountain Dwarf']:
        race = "dwarf"
    elif race == 'Grey Dwarf':
        race = 'duergar'
    elif race in ['Fallen Aasimar', 'Protector Aasimar', 'Scourge Aasimar']:
        race = 'aasimar'
    elif race == 'Eladrin Elf':
        race = 'eladrin'
    elif race in ['High Elf', 'Sea Elf', 'Shadar-Kai Elf', 'Wood Elf']:
        race = 'elf'
    elif race in ['Air Genasi', 'Earth Genasi', 'Fire Genasi', 'Water Genasi']:
        race = 'genasi'
    elif race == 'Deep Gnome':
        race = 'deep-gnome'
    elif race in ['Forest Gnome', 'Rock Gnome']:
        race = 'gnome'
    elif race == 'Half Elf':
        race = 'half-elf'
    elif race == 'Half Orc':
        race = 'half-orc'
    elif race in ['Ghostwise Halfling', 'Lightfoot Halfling', 'Stout Halfling']:
        race = 'halfling'
    elif race in ['Beasthide Shifter', 'Longtooth Shifter', 'Swiftstride Shifter']:
        race = 'shifter'
    elif race == "Simic Hybrid":
        race = 'simic-hybrid'
    elif race in ['Tiefling', 'Feral Tiefling']:
        race = 'tiefling'
    elif race == 'Yuan-ti Pureblood':
        race = 'yuan-ti'

    androg_races = ['aarakocra', 'bugbear', 'changeling', 'genasi', 'hobgoblin', 'kenku', 'kobold', 'lizardfolk', 'tabaxi', 'tortle', 'verdan', 'warforged', 'yuan-ti']

    race = race.lower()

    os.environ['PATH'] += r'C:\Users\hills\Downloads\chromedriver_win32'
    driver = webdriver.Chrome()
    driver.get(f'https://www.fantasynamegenerators.com/dnd-{race}-names.php')
    driver.implicitly_wait(8)

    if name == "Random":
            for race in androg_races:
                result_div = driver.find_element("id", "result")
                androg_names = result_div.text
                nonbinarynames += androg_names.split('\n')
                name = random.choice(nonbinarynames)

            if gender == "Male" and race not in androg_races:
                male_button = driver.find_element("xpath","//input[@value = 'Male names']")
                male_button.click()

                result_div = driver.find_element("id", "result")
                male_names = result_div.text
                malenames += male_names.split('\n')
                name = random.choice(malenames)
                
            elif gender == "Female" and race not in androg_races:
                female_button = driver.find_element("xpath","//input[@value = 'Female names']")
                female_button.click()

                result_div = driver.find_element("id", "result")
                female_names = result_div.text
                femalenames += female_names.split('\n')
                name = random.choice(femalenames)

            elif gender == "Non-Binary" and race not in androg_races:
                male_button = driver.find_element("xpath","//input[@value = 'Male names']")
                male_button.click()

                result_div = driver.find_element("id", "result")
                male_names = result_div.text
                nonbinarynames += male_names.split('\n')

                female_button = driver.find_element("xpath","//input[@value = 'Female names']")
                female_button.click()

                result_div = driver.find_element("id", "result")
                female_names = result_div.text
                nonbinarynames += female_names.split('\n')

                name = random.choice(nonbinarynames)

    return name
         

def getClass():
    charClass = ""
    print("Please select your character's class, if you wish to have this randomly generated. type 'Random'")
    charClass = input("Class:").title()

    while charClass not in classes:
        if charClass == "Random":
            charClass = random.choice(classes)
        else:
            print("Please select a valid class")
            return getClass()
    return charClass

def getStats(race, charClass):
    standardArray = [15, 14, 13, 12, 10, 8]  # Define the standard array of values
    stats = {'STR':0,'DEX':0,'CON':0,'INT':0,'WIS':0,'CHA':0}  # Initialize the stats dictionary
    scores = [] #Empty list for stat scores to be held

    print("You may choose to have your stats assigned randomly, or manually. Input 'R' for random, and 'M' for manual")
    choice = input("R/M: ").title()

    if choice == "M":
        for stat in stats:# Loop through each stat
            while True:  #While True, runs infinately until broken. Upon getting a valid value for a stat within the stats dict it breaks. The for loop re runs it for
                         #each stat within the dictionary, as for stat in stats iterates through the dictionary keys.
                try: #Try and except is needed because the function will break if a non int value is entered for the sta input. Try and except prevents this
                    value = int(input(f"Please assign a value of {standardArray} to {stat}: "))  # Prompt the user for input
                    if value not in standardArray:  # Check if the value is in the standard array
                        print("Invalid value. Please select a value from the standard array.")

                    elif value in stats.values():  # Check if the value has already been assigned to another stat via each key's value
                        print("Value already assigned. Please select a different value.")

                    else:
                        stats[stat] = value  # Assign the value to the current stat
                        standardArray.remove(value) #Remove stats from standard array list, so it doesn't appear in next stat loop
                        break  # Break out of the loop and move on to the next stat
                except ValueError:  # Handle invalid input that can't be converted to an int
                    print("Invalid input. Please enter a number.")

    elif choice == "R":
        for x in range(6): #Outer loop to iterate through inner loop 6 times
            score = [] #Empty list to hold one scores created from inner loop

            for x in range(4): #Inner loop to iterate through 6 sided die 4 times
                score.append(random.randint(1,6)) #Selecting a random # 1-6, and appending that selection to the 'score' list above 4 times

        #Back to the outer loop
            score = sorted(score) #Sorts the 4 'dice' rolls lowest to high
            score.pop(0) #Remove the lowet value from the score list
            scores.append(sum(score)) #Adding the added 3 remaining dice rolls together, and adding that summation of dice rolls to the scores list at the top
        scores = sorted(scores) #Sorts the 6 stats rolls lowest to high

        match charClass:
            case "Fighter":
                stats["STR"] = scores[5]
                stats["CON"] = scores[4]
                stats["DEX"] = scores[3]
                stats["WIS"] = scores[2]
                stats["CHA"] = scores[1]
                stats["INT"] = scores[0]
            case "Wizard":
                stats["STR"] = scores[0]
                stats["CON"] = scores[4]
                stats["DEX"] = scores[3]
                stats["WIS"] = scores[2]
                stats["CHA"] = scores[1]
                stats["INT"] = scores[5]
            case "Rogue":
                stats["STR"] = scores[0]
                stats["CON"] = scores[4]
                stats["DEX"] = scores[5]
                stats["WIS"] = scores[3]
                stats["CHA"] = scores[2]
                stats["INT"] = scores[1]
            case "Barbarian":
                stats["STR"] = scores[5]
                stats["CON"] = scores[4]
                stats["DEX"] = scores[3]
                stats["WIS"] = scores[2]
                stats["CHA"] = scores[1]
                stats["INT"] = scores[0]
            case "Bard":
                stats["STR"] = scores[0]
                stats["CON"] = scores[3]
                stats["DEX"] = scores[4]
                stats["WIS"] = scores[2]
                stats["CHA"] = scores[5]
                stats["INT"] = scores[1]
            case "Cleric":
                stats["STR"] = scores[1]
                stats["CON"] = scores[4]
                stats["DEX"] = scores[3]
                stats["WIS"] = scores[5]
                stats["CHA"] = scores[2]
                stats["INT"] = scores[0]
            case "Druid":
                stats["STR"] = scores[0]
                stats["CON"] = scores[4]
                stats["DEX"] = scores[3]
                stats["WIS"] = scores[5]
                stats["CHA"] = scores[1]
                stats["INT"] = scores[2]
            case "Monk":
                stats["STR"] = scores[2]
                stats["CON"] = scores[4]
                stats["DEX"] = scores[5]
                stats["WIS"] = scores[3]
                stats["CHA"] = scores[0]
                stats["INT"] = scores[1]
            case "Paladin":
                stats["STR"] = scores[5]
                stats["CON"] = scores[4]
                stats["DEX"] = scores[3]
                stats["WIS"] = scores[1]
                stats["CHA"] = scores[2]
                stats["INT"] = scores[0]
            case "Ranger":
                stats["STR"] = scores[0]
                stats["CON"] = scores[4]
                stats["DEX"] = scores[5]
                stats["WIS"] = scores[3]
                stats["CHA"] = scores[2]
                stats["INT"] = scores[1]
            case "Sorcerer":
                stats["STR"] = scores[0]
                stats["CON"] = scores[3]
                stats["DEX"] = scores[4]
                stats["WIS"] = scores[2]
                stats["CHA"] = scores[5]
                stats["INT"] = scores[1]
            case "Warlock":
                stats["STR"] = scores[0]
                stats["CON"] = scores[3]
                stats["DEX"] = scores[4]
                stats["WIS"] = scores[1]
                stats["CHA"] = scores[5]
                stats["INT"] = scores[2]
            case "Artificer":
                stats["STR"] = scores[1]
                stats["CON"] = scores[4]
                stats["DEX"] = scores[3]
                stats["WIS"] = scores[2]
                stats["CHA"] = scores[0]
                stats["INT"] = scores[5]
            case "Bloodhunter":
                stats["STR"] = scores[2]
                stats["CON"] = scores[4]
                stats["DEX"] = scores[5]
                stats["WIS"] = scores[3]
                stats["CHA"] = scores[0]
                stats["INT"] = scores[1]
    return stats

class Character:
    def _init_(self):
        pass
    
    def createCharacter(self):
        race = getRace()
        gender = getGender()
        name = getName(race, gender)
        charClass = getClass()
        stats = getStats(race, charClass)
        print("\n")
        print("Your New Character:")
        print("_________________________________________________________________")
        print(race)
        print(gender)
        print(name)
        print(charClass)
        print(stats)
        print("__________________________________________________________________")
        print("\n")
Character().createCharacter()



