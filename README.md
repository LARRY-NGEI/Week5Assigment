# Week5Assigment
class Superhero:
    def __init__(self, name, secret_identity, power_level):
        self._name = name  # Protected attribute
        self.__secret_identity = secret_identity  # Private attribute
        self.power_level = power_level
        self._villains_defeated = 0

    # Encapsulated getter for secret identity
    def reveal_secret_identity(self):
        return f"My real name is {self.__secret_identity}"

    def fight_villain(self, villain_power):
        if self.power_level > villain_power:
            self._villains_defeated += 1
            return f"{self._name} defeated the villain!"
        else:
            return f"{self._name} was outmatched this time..."

    def get_villains_defeated(self):
        return self._villains_defeated

    def __str__(self):
        return f"{self._name} (Power: {self.power_level})"


class TechHero(Superhero):
    def __init__(self, name, secret_identity, power_level, gadget):
        super().__init__(name, secret_identity, power_level)
        self.gadget = gadget

    def use_gadget(self):
        self.power_level += 15  # Gadgets give temporary power boost
        return f"{self._name} uses {self.gadget}! Power increased!"

    def fight_villain(self, villain_power):  # Polymorphism
        result = super().fight_villain(villain_power)
        return f"⚡ Tech-Assisted Battle ⚡\n{result}"


class MagicHero(Superhero):
    def __init__(self, name, secret_identity, power_level, spell):
        super().__init__(name, secret_identity, power_level)
        self.spell = spell

    def cast_spell(self):
        return f"✨ {self._name} casts {self.spell}! ✨"

    def fight_villain(self, villain_power):  # Polymorphism
        if "dark" in self.spell.lower():
            villain_power *= 0.8  # Dark magic weakens villains
        return super().fight_villain(villain_power)


# Demonstration
if __name__ == "__main__":
    print("=== Superhero Showcase ===")
    
    iron_man = TechHero("Iron Man", "Larry Ngei", 85, "Repulsor Beams")
    dr_mutua = MagicHero("Doctor Mutua", "Stephen Mutua", 90, "Crimson Bands of Cyttorak")
    
    print(iron_man)
    print(dr_mutua)
    
    print("\n" + iron_man.use_gadget())
    print(dr_mutua.cast_spell())
    
    print("\n" + iron_man.fight_villain(95))
    print(dr_mutua.fight_villain(100))
    
    print("\nSecret Identities:")
    print(iron_man.reveal_secret_identity())
    print(dr_mutua.reveal_secret_identity())
    
  #Activity two

class Vehicle:
    def __init__(self, name, speed):
        self.name = name
        self.speed = speed
    
    def move(self):
        raise NotImplementedError("Subclasses must implement this method")
    
    def __str__(self):
        return f"{self.name} (Max speed: {self.speed} km/h)"


class Car(Vehicle):
    def move(self):
        return f"🚗 {self.name} is driving at {self.speed} km/h (Vroom vroom!)"
    
    def honk(self):
        return "🔊 Beep beep!"


class Airplane(Vehicle):
    def move(self):
        return f"✈️ {self.name} is flying at {self.speed} km/h (Whoosh!)"
    
    def take_off(self):
        return "🛫 Preparing for takeoff..."


class Boat(Vehicle):
    def move(self):
        return f"⛵ {self.name} is sailing at {self.speed} km/h (Splish splash!)"
    
    def anchor(self):
        return "⚓ Dropping anchor!"


class Bicycle(Vehicle):
    def move(self):
        return f"🚴 {self.name} is pedaling at {self.speed} km/h (Ring ring!)"
    
    def do_wheelie(self):
        return "🚲 Whoa! Doing a wheelie!"


# Demonstration
if __name__ == "__main__":
    print("=== Vehicle Movement Showcase ===")
    
    vehicles = [
        Car("Mazda cx5", 250),
        Airplane("Kenya Airways", 900),
        Boat("Kifaru", 56),
        Bicycle("Mountain Bike", 30)
    ]
    
    for vehicle in vehicles:
        print("\n" + str(vehicle))
        print(vehicle.move())
        
        # Demonstrate unique methods
        if isinstance(vehicle, Car):
            print(vehicle.honk())
        elif isinstance(vehicle, Airplane):
            print(vehicle.take_off())
        elif isinstance(vehicle, Boat):
            print(vehicle.anchor())
        elif isinstance(vehicle, Bicycle):
            print(vehicle.do_wheelie())



  
