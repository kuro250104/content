Le modèle flyweight fait partie de la catégorie des modèles de conception structurels. Il fournit un moyen de réduire le nombre d'objets. Il comprend diverses caractéristiques qui permettent d'améliorer la structure des applications. La caractéristique la plus importante des objets flyweight est leur caractère immuable. Cela signifie qu'ils ne peuvent pas être modifiés une fois construits. Ce modèle utilise un HashMap pour stocker les objets de référence.

## Comment mettre en œuvre le modèle flyweight ?

Le programme suivant aide à mettre en œuvre le modèle flyweight :

```python
class ComplexGenetics(object):
    def __init__(self):
        pass

    def genes(self, gene_code):
        return "ComplexPatter[%s]TooHugeinSize" % (gene_code)

class Families(object):
    family = {}

    def __new__(cls, name, family_id):
        try:
            id = cls.family[family_id]
        except KeyError:
            id = object.__new__(cls)
            cls.family[family_id] = id
        return id

    def set_genetic_info(self, genetic_info):
        cg = ComplexGenetics()
        self.genetic_info = cg.genes(genetic_info)

    def get_genetic_info(self):
        return (self.genetic_info)

def test():
    data = (('a', 1, 'ATAG'), ('a', 2, 'AAGT'), ('b', 1, 'ATAG'))
    family_objects = []
    for i in data:
        obj = Families(i[0], i[1])
        obj.set_genetic_info(i[2])
        family_objects.append(obj)
    
    for i in family_objects:
        print "id = " + str(id(i))
        print i.get_genetic_info()
    print("similar id's says that they are same objects")

if __name__ == '__main__':
    test()
```

## Résultat

Le programme ci-dessus génère la réponse suivante :

```bash
id = 25670608
ComplexPatter[ATAG]TooHugeinSize
id = 25670544
ComplexPatter[ATAG]TooHugeinSize
id = 25670608
ComplexPatter[ATAG]TooHugeinSize
similar id's says that they are same objects
```
