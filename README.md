class Superhero:
    def __init__(self, name, secret_identity, powers, weakness):
        self.name = name
        self.secret_identity = secret_identity
        self.powers = powers  # List of powers
        self.weakness = weakness
        self.energy_level = 100
        
    def use_power(self, power_index):
        if power_index < len(self.powers):
            print(f"{self.name} uses {self.powers[power_index]}!")
            self.energy_level -= 10
        else:
            print("Power not available!")
    
    def rest(self):
        print(f"{self.name} is resting to recover energy")
        self.energy_level = min(100, self.energy_level + 30)
        
    def __str__(self):
        return f"{self.name} (Secret ID: {self.secret_identity})"

# Inheritance example
class Sidekick(Superhero):
    def __init__(self, name, secret_identity, powers, weakness, mentor):
        super().__init__(name, secret_identity, powers, weakness)
        self.mentor = mentor
        
    def call_for_help(self):
        print(f"{self.name} calls {self.mentor} for backup!")
        self.energy_level += 20  # Gets motivated by mentor

# Usage
hero = Superhero("Thunderstrike", "Alex Johnson", 
                ["Lightning Blast", "Super Speed"], "Rubber")
sidekick = Sidekick("Spark", "Jamie Chen", 
                   ["Small Shock", "Quick Dodge"], "Water", "Thunderstrike")

print(hero)
hero.use_power(0)  # Uses Lightning Blast
print(f"Energy left: {hero.energy_level}")

print("\n" + str(sidekick))
sidekick.call_for_help()
class Animal:
    def __init__(self, name):
        self.name = name
        
    def move(self):
        pass  # Abstract method

class Fish(Animal):
    def move(self):
        return f"{self.name} is swimming!"

class Bird(Animal):
    def move(self):
        return f"{self.name} is flying!"

class Snake(Animal):
    def move(self):
        return f"{self.name} is slithering!"

# Polymorphism in action
animals = [
    Fish("Nemo"),
    Bird("Eagle"),
    Snake("Viper")
]

for animal in animals:
    print(animal.move())
