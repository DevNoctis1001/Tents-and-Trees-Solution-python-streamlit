# Tents and Trees puzzle with Python and Streamlit

This is a project to implement a "Tents and Trees" puzzle in Python.
The Tents (also known as "Tents and Trees") is a popular logic puzzle. 

According to https://wpcunofficial.miraheze.org/wiki/Tents, the puzzle was first published in 1989 by Léon Balmaekers under the name "Alen Verzamelen" in Dutch.
The rules of the puzzle are as follows:
    
    •	Find all of the tents in the forest.
    •	Every tent is attached to exactly one tree, and every tree is attached to exactly one tent.
    •	The number of tents is the same as the number of trees.
    •	The clues tell you how many tents are in that row or column.
    •	A tent can only be found horizontally or vertically next to a tree.
    •	Tents are never next to each other, neither vertically, horizontally, or diagonally.
    •	A tree might be next to two tents but is only connected to one.

## About the algorithm

I solved this problem using a step-by-step, iterative method.
Each cells of grid may be 4 states : "tree", "tent", "grass", or "not-tested".

The steps of algorithm are as follows:
	
- Check all hints in rows and columns. If you find a row or column with a "0" hint, you can set all cells except for the trees in that row and column to "grass".
- And the rest of the steps are repeated until all tents are found.
  1. Each identified "tree" and "tent" pair is excluded from the iteration. (Assume it is grass.)
     ![image](https://github.com/DevNoctis1001/Tents-and-Trees-Solution-python-streamlit/assets/148486194/de618518-ca6c-4f71-90c6-89583a228a27)

  2. Cells with no trees around them (top, bottom, left, right) are identified as "grass".
     ![image](https://github.com/DevNoctis1001/Tents-and-Trees-Solution-python-streamlit/assets/148486194/b9989db6-8453-45f8-9950-de2f64e15d07)
     
  3. If there is only one 'not-tested' cell around the 'tree', this is the 'tent'.
	![image](https://github.com/DevNoctis1001/Tents-and-Trees-Solution-python-streamlit/assets/148486194/a8fe3f10-c2ab-448f-8b02-d8acc83db4a8)

  4. All cells that exist around the cell identified as "tent" are set to "grass".
  5. Check each hint and its rows and columns to determine the location and number of possible tents. Based on this information, make the identified cells into "tents".
     ![image](https://github.com/DevNoctis1001/Tents-and-Trees-Solution-python-streamlit/assets/148486194/e9263717-94bb-4fc7-8cd2-66c5eac5e0f1)

  
  6. Make the cells that exist around the new 'tent'(up, down, left, right) the 'grass'.
     
     Also, if the current number of 'tents' in any row or column is equal to the hint, all remaining 'not-tested' cells become 'grass'.
  7. See Hints and special location cases, cells that can't be 'tents' are set to 'grass'.

     Like this:
     ![image](https://github.com/DevNoctis1001/Tents-and-Trees-Solution-python-streamlit/assets/148486194/e22574d9-2d3a-4f80-b524-a93c441f0484)

  8. check all the corners(meaning in subset) and "grass" the impossible ones.
     ![image](https://github.com/DevNoctis1001/Tents-and-Trees-Solution-python-streamlit/assets/148486194/7c61b19b-820c-4a12-89ed-43fd64c1b3f4)

When you repeat this step, if the algorithm is satisfied with one step, it runs it again, starting from the first step. This is iterative method.

I don't think any one of breadth-first search, depth-first search, or others can solve this sensitive problem.

## User Interface

And the UI is built with streamlit.  

Streamlit is a powerful tool to create web UI with python for data science and AI. 

![image](https://github.com/DevNoctis1001/Tents-and-Trees-Solution-python-streamlit/assets/148486194/b2defaa2-73ee-4f5f-b0aa-b3ebdbd15777)

![image](https://github.com/DevNoctis1001/Tents-and-Trees-Solution-python-streamlit/assets/148486194/0f81964a-1be7-4d99-aeaf-b1dd87a6733a)




