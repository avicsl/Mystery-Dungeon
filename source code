#include <iostream>
#include <vector>
#include <cstdlib>
#include <ctime>
#include <string>

using namespace std;

class Room {
public:
    string description;
    bool hasMonster;
    bool hasTreasure;

    Room(string desc, bool monster, bool treasure)
        : description(desc), hasMonster(monster), hasTreasure(treasure) {}
};

class Player {
public:
    string name;
    int health;
    int treasure;

    Player(string playerName) : name(playerName), health(100), treasure(0) {}

    void displayStatus() {
        cout << "Player: " << name << " | Health: " << health << " | Treasure: " << treasure << endl;
    }
};

class Game {
private:
    Player player;
    vector<Room> dungeon;
    int currentRoom;

public:
    Game(string playerName) : player(playerName), currentRoom(0) {
        initializeDungeon();
    }

    void initializeDungeon() {
        dungeon.push_back(Room("You are in a dark room. There's a faint light ahead.", false, true));
        dungeon.push_back(Room("You enter a room filled with cobwebs. A monster appears!", true, false));
        dungeon.push_back(Room("This room is empty, but you feel a chill in the air.", false, false));
        dungeon.push_back(Room("You find a treasure chest! It's filled with gold!", false, true));
        dungeon.push_back(Room("A monster lurks in the shadows. Prepare to fight!", true, false));
    }

    void play() {
        cout << "Welcome to the Mystery Dungeon, " << player.name << "!" << endl;

        while (player.health > 0 && currentRoom < dungeon.size()) {
            player.displayStatus();
            cout << dungeon[currentRoom].description << endl;

            if (dungeon[currentRoom].hasMonster) {
                cout << "A monster attacks you!" << endl;
                player.health -= 20; // Simple combat mechanic
                cout << "You lost 20 health!" << endl;
            }

            if (dungeon[currentRoom].hasTreasure) {
                cout << "You found treasure!" << endl;
                player.treasure += 50; // Collect treasure
            }

            currentRoom++;
            if (currentRoom < dungeon.size()) {
                cout << "You move to the next room..." << endl;
            }
        }

        if (player.health <= 0) {
            cout << "You have been defeated. Game Over!" << endl;
        } else {
            cout << "Congratulations! You've explored the dungeon!" << endl;
            cout << "Total Treasure Collected: " << player.treasure << endl;
        }
    }
};

int main() {
    srand(static_cast<unsigned int>(time(0))); // Seed for random number generation
    string playerName;

    cout << "Enter your name: ";
    getline(cin, playerName);

    Game game(playerName);
    game.play();

    return 0;
}
