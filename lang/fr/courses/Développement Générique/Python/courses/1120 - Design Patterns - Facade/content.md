Le design pattern Facade fournit une interface unifiée à un ensemble d'interfaces dans un sous-système. Il définit une interface de niveau supérieur que tout sous-système peut utiliser.

Une classe de façade sait quel sous-système est responsable d'une demande.

## Comment concevoir un modèle facade ?

Voyons maintenant comment concevoir un motif de facade.

```python
class _IgnitionSystem(object):

    @staticmethod
    def produce_spark():
        return True

class _Engine(object):

    def __init__(self):
        self.revs_per_minute = 0

    def turnon(self):
        self.revs_per_minute = 2000

    def turnoff(self):
        self.revs_per_minute = 0

class _FuelTank(object):

    def __init__(self, level=30):
        self._level = level

    @property
    def level(self):
        return self._level

    @level.setter
    def level(self, level):
        self._level = level

class _DashBoardLight(object):

    def __init__(self, is_on=False):
        self._is_on = is_on

    def __str__(self):
        return self.__class__.__name__

    @property
    def is_on(self):
        return self._is_on

    @is_on.setter
    def is_on(self, status):
        self._is_on = status

    def status_check(self):
        if self._is_on:
            print("{}: ON".format(str(self)))
        else:
            print("{}: OFF".format(str(self)))

class _HandBrakeLight(_DashBoardLight):
    pass

class _FogLampLight(_DashBoardLight):
    pass

class _Dashboard(object):

    def __init__(self):
        self.lights = {"handbreak": _HandBrakeLight(), "fog": _FogLampLight()}

    def show(self):
        for light in self.lights.values():
            light.status_check()

# Facade
class Car(object):

    def __init__(self):
        self.ignition_system = _IgnitionSystem()
        self.engine = _Engine()
        self.fuel_tank = _FuelTank()
        self.dashboard = _Dashboard()

    @property
    def km_per_litre(self):
        return 17.0

    def consume_fuel(self, km):
        litres = min(self.fuel_tank.level, km / self.km_per_litre)
        self.fuel_tank.level -= litres

    def start(self):
        print("\nStarting...")
        self.dashboard.show()
        if self.ignition_system.produce_spark():
            self.engine.turnon()
        else:
            print("Can't start. Faulty ignition system")

    def has_enough_fuel(self, km, km_per_litre):
        litres_needed = km / km_per_litre
        if self.fuel_tank.level > litres_needed:
            return True
        else:
            return False

    def drive(self, km = 100):
        print("\n")
        if self.engine.revs_per_minute > 0:
            while self.has_enough_fuel(km, self.km_per_litre):
                self.consume_fuel(km)
            print("Drove {}km".format(km))
            print("{:.2f}l of fuel still left".format(self.fuel_tank.level))
        else:
            print("Can't drive. The Engine is turned off!")

    def park(self):
        print("\nParking...")
        self.dashboard.lights["handbreak"].is_on = True
        self.dashboard.show()
        self.engine.turnoff()

    def switch_fog_lights(self, status):
        print("\nSwitching {} fog lights...".format(status))
        boolean = True if status == "ON" else False
        self.dashboard.lights["fog"].is_on = boolean
        self.dashboard.show()

    def fill_up_tank(self):
        print("\nFuel tank filled up!")
        self.fuel_tank.level = 100

# the main function is the Client
def main():
    car = Car()
    car.start()
    car.drive()
    car.switch_fog_lights("ON")
    car.switch_fog_lights("OFF")
    car.park()
    car.fill_up_tank()
    car.drive()
    car.start()
    car.drive()

if __name__ == "__main__":
    main()
```

### Résultat

Le programme ci-dessus génère le résultat suivant :

```bash
Starting...
_HandBrakeLight: OFF
_FogLampLight: OFF


Drove 100km
0.59l of fuel still left

Switching ON fog lights...
_HandBrakeLight: OFF
_FogLampLight: ON

Switching OFF fog lights...
_HandBrakeLight: OFF
_FogLampLight: OFF

Parking...
_HandBrakeLight: ON
_FogLampLight: OFF

Fuel tank filled up!


Can't drive. The Engine is turned off!

Starting...
_HandBrakeLight: ON
_FogLampLight: OFF


Drove 100km
0.00l of fuel still left
```

### Explication

Ce programme est conçu avec un scénario. C'est celui du démarrage du moteur d'une voiture ou de tout autre véhicule à moteur. Si vous observez le code, il comprend les fonctions associées pour conduire, se garer et consommer du carburant également.
