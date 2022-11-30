# La course de dé (version JavaFX)

L'objectif de ce TP est d'ajouter une interface graphique au jeu de dé que vous avez codé en C++ en première année. Pour rappel :

>  La « course de dé » se joue en lançant un dé. Les joueurs jouent tour à tour (pour ce TP nous nous limiterons à deux joueurs). Lorsque c'est à son tour, le joueur lance un dé et, tant qu'il ne fait pas 1, accumule les points des lancers successifs. S'il fait 1, il perd les points qu'il avait accumulés pendant son tour de jeu et la main passe, c'est à l'autre joueur de jouer. Un joueur peut sciemment décider d'arrêter de lancer le dé et ainsi sécuriser le score de son tour de jeu. Le premier joueur qui atteint un score de victoire (par exemple 50) gagne.

Afin de vous concenter sur l'interface graphique, nous vous fournissons la version Java du jeu que vous avez codé en C++. La conception de ce dernier est rappelé ci-dessous.

```plantuml
@startuml
skinparam defaultFontName Tahoma
skinparam classAttributeIconSize 0
skinparam monochrome true
skinparam shadowing false
skinparam linetype ortho
skinparam class {
    BackgroundColor transparent
}
skinparam package {
    BackgroundColor transparent
}
hide circle

package launcher {

class ConsoleGame {
    +{static} main(args : String[])
}

}

package model {

class Dice {
    -{static}NB_FACES_DEFAULT : int = 6 {frozen}
    -nbFaces : int
    -value : int

    +Dice(nbFaces : int)
    +Dice()
    +getValue() : int
    +roll() : int
    +clear()
}

class Player {
    -{static}num : int = 0
    -name : string
    -totalScore : int
    -currentScore : int

    +Player(name : string)
    +Player()
    +getName() : string
    +getCurrentScore() : int
    +setCurrentScore(score : int)
    +getTotalScore() : int
    +setTotalScore(score : int)
}

class Game {
    +{static}LOSE_DICE_VALUE : int = 1 {frozen}
    +{static}SCORE_TO_WIN : int = 50 {frozen}
    -gameOver : boolean
    -currentPlayerIndex : int

    +Game()
    +addPlayer(player : Player)
    +getCurrentPlayer() : Player
    +rollDice()
    +getDiceValue() : int
    +isGameOver() : boolean
    +passToNextPlayer()
    +restart()
}

Game --> "-dice" Dice
Game --> "*\n-players" Player
ConsoleGame ..> Game

}

@enduml
```

