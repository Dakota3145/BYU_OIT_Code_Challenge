# BYU_OIT_Code_Challenge
  This is the text of the code found in the .ipynb file if you're having troubles viewing that file...
  
import numpy as np

romanNumerals = np.array(['I', 'V', 'X', 'L', 'C', 'D', 'M'])

romanValues = np.array([1, 5, 10, 50, 100, 500, 1000])
def romanToDecimal(romanString):
  decimalTotal = 0
  numValue = 0
  i = 0
  while i < len(romanString):
    currentRomanIndex = np.where(romanNumerals==romanString[i])[0]
    if(i < len(romanString) - 1):
      nextRomanIndex = np.where(romanNumerals==romanString[i + 1])[0]
      if (nextRomanIndex > currentRomanIndex):
        numValue = romanValues[nextRomanIndex] - romanValues[currentRomanIndex]
        i += 1
      else:
        numValue = romanValues[currentRomanIndex]
    else:
      numValue = romanValues[currentRomanIndex]
    decimalTotal += numValue
    i += 1
  print(romanString, " converted to decimal is ", decimalTotal)
def decimalToRoman(number):
  strOfNum = str(number)
  finalRomanString = ""
  for i in range(len(strOfNum)):
    decimalNumber = int(strOfNum[i])
    numZeroes = (len(strOfNum) - 1) - i
    romanString = ""
    romanIndex = numZeroes * 2
    if (decimalNumber == 9):
      oneNumeral = romanNumerals[romanIndex]
      romanString += oneNumeral
      tenNumeral = romanNumerals[romanIndex + 2]
      romanString += tenNumeral
    if (decimalNumber > 4 and decimalNumber < 9):
      romanString += romanNumerals[romanIndex + 1]
      decimalNumber -= 5
    if (decimalNumber < 4):
      romanIndex = numZeroes * 2
      for _ in range(decimalNumber):
        romanString += romanNumerals[romanIndex]
    finalRomanString += romanString
  print(number, "converted to Roman Numerals is ", finalRomanString)
romanToDecimal("CLXV")
decimalToRoman(93)
