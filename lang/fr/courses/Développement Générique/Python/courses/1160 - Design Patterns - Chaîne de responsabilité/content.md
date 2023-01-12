Le modèle de chaîne de responsabilité est utilisé pour réaliser un couplage lâche dans un logiciel où une demande spécifique du client est transmise à travers une chaîne d'objets inclus dans celle-ci. Il permet de construire une chaîne d'objets. La demande entre par une extrémité et passe d'un objet à l'autre.

Ce modèle permet à un objet d'envoyer une commande sans savoir quel objet traitera la demande.

## Comment mettre en œuvre le modèle de la chaîne de responsabilité ?

Nous allons maintenant voir comment mettre en œuvre le modèle de la chaîne de responsabilité.

```python
class ReportFormat(object):
    PDF = 0
    TEXT = 1
class Report(object):
    def __init__(self, format_):
        self.title = 'Monthly report'
        self.text = ['Things are going', 'really, really well.']
        self.format_ = format_

class Handler(object):
    def __init__(self):
        self.nextHandler = None

    def handle(self, request):
        self.nextHandler.handle(request)

class PDFHandler(Handler):

    def handle(self, request):
        if request.format_ == ReportFormat.PDF:
            self.output_report(request.title, request.text)
        else:
            super(PDFHandler, self).handle(request)

    def output_report(self, title, text):
        print('<html>')
        print(' <head>')
        print(' <title>%s</title>' % title)
        print(' </head>')
        print(' <body>')
        for line in text:
            print(' <p>%s' % line)
        print(' </body>')
        print('</html>')

class TextHandler(Handler):

    def handle(self, request):
        if request.format_ == ReportFormat.TEXT:
            self.output_report(request.title, request.text)
        else:
            super(TextHandler, self).handle(request)

    def output_report(self, title, text):
        print(5 * '*' + title + 5 * '*')
        for line in text:
            print(line)

class ErrorHandler(Handler):
    def handle(self, request):
        print("Invalid request")

if __name__ == '__main__':
    report = Report(ReportFormat.TEXT)
    pdf_handler = PDFHandler()
    text_handler = TextHandler()

    pdf_handler.nextHandler = text_handler
    text_handler.nextHandler = ErrorHandler()
	pdf_handler.handle(report)
```

### Résultat

Le programme ci-dessus génère le résultat suivant :

```bash
*****Monthly report*****
Things are going
really, really well.
```

### Explication

Le code ci-dessus crée un rapport pour les tâches mensuelles où il envoie des commandes à travers chaque fonction. Il prend deux gestionnaires - pour le PDF et pour le texte. Il imprime la sortie une fois que l'objet requis exécute chaque fonction.
