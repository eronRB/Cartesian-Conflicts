# Cartesian Conflicts


### Project Title or Name of the Application	: Cartesian Conflicts
### Section			   	      : Rubidium
### Group Members			    : Bautista, Belcena, Pequiro
### Date (Proposal Date)  : Nov 13, 2026

### Project Description:

- A brief summary of the project description and the need for it.
  
  Cartesian Conflicts is an educational and turn-based game set on the lands of the Abscissa and Ordinate, an imaginary dimension governed by the realm of Pure Mathematica. A few months ago, bot agents known as the Astra Bots, led by the evil and manipulative SAMALT ZERO, invaded the coordinate system, threatening to replace the stability of Pure Mathematica preserved from generation to generation. As the Function Warden, the player needs to destroy the numerous Astra bots and eliminate the final boss. To eliminate the bots, players fire lasers across the graph.
      
  To attack the bots, mathematical functions are needed instead of setting the angles and power of your laser. However, these bot agents are feeding off of these attacks to learn how to attack you against your own ability, so learning how to adapt faster than these bots are needed.
    
- Describes system components, features, and expected outputs clearly and logically. NOTE: Clearly described the elements(classes), their attributes and methods and how they will interact with each other.
  
    The game includes a 2D coordinate grid board, player and bot health bars, a reasoning engine for the Astra Bots, and a turn based system. The expected output is a fully playable 2D game where players advance through waves of enemies using mathematical functions, adapting their equations to counter different bot formations and defensive strategies before confronting and defeating the boss to win.

  The classes include the: 
  
  - GameObject(Attributes: x (float), y (float) Methods: update_position(x, y)) 
 
  - GraphType(Attributes: name (string) Methods: evaluate(x)) 
  
  - DynamicGraph(Attributes: expression (string) Methods: evaluate(x)) 
  
  - GraphEntity(Attributes: hp (int), damage_value(int), coordinates(list) Methods: assign_coordinate(x, y), calculate_graph_damage()) 
  
  - Team(Methods: collect_user_input_coordinates()) 
  
   - Enemy(Methods: collect_enemy_coordinates(target_x, target_y)) 
  
   - GameManager(Methods: startGame(), switchTurn()) 
  
   - GameBoard(Methods: renderEntities(List entities), drawGrid()) 

  The GameManager controls the flow of the game like Team, Enemy, and GameBoard. During the player's turn, the Team collects user input to plot points and when an attack executes the system uses calculate_graph_damge() to run these plotted coordinates through the DynamicGraph's evaluate() method. On the AI's turn, the Enemy automatically generates its own attack coordinates using collect_enemy_coordinates() based on its assigned graph logic.
- Include the description as well of your target demographics as the user of your application.
  
    The primary target users are middle school, high school, and college students who are learning concepts related to algebra, geometry, pre-calculus, and some topics related to calculus.

- The description is then followed by the class diagram, depicting clearly what was described.
```mermaid
classDiagram
    class GameObject {
      -x : Float
      -y : Float
      +update_position(float x, float y)
    }
    
    class GraphType {
      <<abstract>>
      -name : String
      +evaluate(float x) 
    }
    
    class DynamicGraph {
      -expression : String
      +evaluate(float x) 
    }
    
    class GraphEntity {
      -hp : Int
      -damage_ value : Int
      -coordinates : List
      +assign_coordinate(float x, float y)
      +calculate_graph_damage() 
    }
    
    class Team {
      +collect_user_input_coordinates()
    }
    
    class Enemy {
      +collect_enemy_coordinates(float target_x, float target_y)
    }

    class GameManager {
      +startGame()
      +switchTurn()
    }

    class GameBoard {
      +renderEntities(List entities)
      +drawGrid()
    }

    GameObject <|-- GraphEntity
    GraphType <|-- DynamicGraph
    
    GraphEntity "1" *-- "1" GraphType : utilizes
    GraphEntity <|-- Team
    GraphEntity <|-- Enemy
    
    GameManager "1" --> "1" GameBoard : controls
    GameManager "1" --> "1" Team : manages
    GameManager "1" --> "1..*" Enemy : manages
    GameBoard "1" --> "0..*" GameObject : renders
```

### Goals:

The goal of Cartesian Conflicts is to make people, including ourselves, increase their mathematic literacy and improve their intuitive understanding of functions. Cartesian Conflicts should also be a reliable and educational game that is almost entirely bug free.

Describe the long term outcomes of your project followed by a couple of objectives to meet the goals stated in this paragraph

- Objective 1: A functional cartesian plane (game board) that can render almost any function. 
- Objective 2: The program can accurately evaluate the user inputs and catch syntax errors
- Objective 3: Program at least three distinct AstraBot profiles that can generate valid mathematical attacks based on their assigned method of attacking 
- Objective 4: Make a complete, bug-free single-player game loop that has level progression and collision detection. 
