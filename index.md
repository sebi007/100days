# ERP in 100 Tagen

## 001 Datenbankschema: Artikel

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day1.png)

## 002 Datenbankschema: Kundentabelle

Heute habe ich mich mit dem Anlegen der Kundentabelle, sowie andere zugehörige Tabellen, wie zum Beispiel zugehörige Adressen.

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day2.png)

## 003 Datenbankschema: Rechnungen Teil 1

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day3.png)

## 004 Datenbankschema: Rechnungen Teil 2

Das Datenbankschema ist vorerst fertig. Als nächstes geht es an die Erstellung der einzelnen Views.

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day4.png)

## 005 Design: Artikelübersicht

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day5.png)

## 006 Design: Artikeldetail

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day6.png)


## 007 Umsetzung: Navigationsleiste

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day7.png)

## 008 Programmierung: API
Heute habe ich die ersten Funktionen der Schnittstelle programmiert, die mir später die Daten an das Frontend liefert.

```php
public function index()
    {
        $articles = Article::all();

        return $this->response->collection($articles, new ArticlesTransformer(), [], function ($resource, $fractal) {
            $fractal->parseIncludes("article_group");
        });
    }
```


```php
class ArticlesTransformer extends TransformerAbstract
    {

        protected $availableIncludes = ["article_group"];

        public function transform(Article $article)
        {
            return [
                "id" => (int) $article->id,
                "sku" => $article->sku,
                "name" => $article->name,
                "description" => $article->description
            ];
        }

        public function includeArticleGroup(Article $article)
        {
            $articleGroup = $article->article_group;

            return $this->item($articleGroup, new ArticleGroupsTransformer());
        }
    }
```
