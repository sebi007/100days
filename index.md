# ERP in 100 Tagen

## 035 Programmierung: Redux Reducer - Artikel

```javascript
const initialState = {
    fetching: false,
    fetched: false,
    articles: [],
    error: null
};

export default function (state = initialState, action) {
    switch (action.type) {
        case "FETCH_ARTICLES":
            return {...state, fetching: true};
            break;
        case "FETCH_ARTICLES_FULFILLED":
            return {...state, fetching: false, fetched: true, articles: action.payload.data};
            break;
        case "FETCH_ARTICLES_REJECTED":
            return {...state, fetching: false, error: action.payload};
        default:
            return state;
            break;
    }
}
```

## 034 Programmierung: Redux Schnittstellenzugriff - Artikel

```javascript
const articleGroupEpic = action$ =>
    action$.ofType("FETCH_ARTICLE_GROUPS")
        .mergeMap(action =>
            ajax.getJSON("http://angular-erp.dev/api/article_groups")
                .map(response => ({type: "FETCH_ARTICLE_GROUPS_FULFILLED", payload: response}))
                .catch(error => Observable.of({
                    type: "FETCH_ARTICLE_GROUPS_REJECTED",
                    payload: error.xhr.response,
                    error: true
                })));
```

## 033 Design: Einstellungen

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day33.png)

## 032 Design: Rechnung - Historie

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day32.png)

## 031 Design: Rechnung - Belegdaten

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day31.png)

## 030 Design: Rechnung - Artikel

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day30.png)

## 029 Design: Rechnung (nicht final)

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day29.png)

## 028 Design: Kunden Detail - Historie

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day28.png)

## 027 Design: Kunden Detail - Adresse

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day27.png)

## 026 Design: Kunden Detail - Neue Adresse

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day26.png)

## 025 Design: Kunden Detail

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day25.png)

## 024 Design: Artikel Detail Historie

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day24.png)

## 023 Design: Artikel Detail Preis

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day23.png)

## 022 Datenbankschema: Logs

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day22.png)

## 021 Design: Belegauswertung

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day21.png)

## 020 Design: Login

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day20_2.png)

## 019 Design: Dashboard

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day19.png)

## 018 Design: Artikelgruppe anlegen

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day18.png)

## 017 Artikelgruppenübersicht - Desktop

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day17.png)

## 016 Programmierung: API

```php
class CustomersController extends Controller
    {

        use Helpers;

        public function index()
        {
            $taxRates = Customer::all();

            return $this->response->collection($taxRates, new CustomerTransformer());
        }

        public function add(CustomerRequest $request)
        {
            if(Customer::create($request->all())) {
                if(AddressSet::create($request->all())) {
                    return $this->response->created();
                }
            }

            return $this->response->errorBadRequest();
        }

        public function get($id)
        {
            $article = Customer::find($id);
            if ($article) {
                return $this->response->item($article, new CustomerTransformer());
            }

            return $this->response->errorNotFound();
        }

    }
```

## 015 Programmierung: API

```php
class TaxRatesController extends Controller
    {
        
        use Helpers;

        public function index()
        {
            $taxRates = TaxRate::all();

            return $this->response->collection($taxRates, new TaxRateTransformer());
        }

        public function add(TaxRateRequest $request)
        {
            if(TaxRate::create($request->all())) {
                return $this->response->created();
            }

            return $this->response->errorBadRequest();
        }

        public function get($id)
        {
            $article = TaxRate::find($id);
            if ($article) {
                return $this->response->item($article, new TaxRateTransformer());
            }

            return $this->response->errorNotFound();
        }
        
    }
```

## 014 Programmierung: API

```php
public function add(ArticleRequest $request)
    {
        if(Article::create($request->all())) {
            return $this->response->created();
        }

        return $this->response->errorBadRequest();
    }

public function get($id)
    {
        $article = Article::find($id);
        if ($article) {
            return $this->response->item($article, new ArticlesTransformer());
        }

        return $this->response->errorNotFound();
    }
```

## 013 Artikelübersicht - Desktop

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day13.png)

## 012 Artikelübersicht - Handy

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day12_2.png)

## 011 Programmierung

Die ersten API Aufrufe aus dem Programm.

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day11.png)

## 010 Programmierung: API

Ein weiterer Teil der API.

```php
    class ArticleGroupsController extends Controller
    {

        use Helpers;

        public function index()
        {
            $articleGroups = ArticleGroup::all();

            return $this->response->collection($articleGroups, new ArticleGroupsTransformer());
        }

        public function add(ArticleGroupRequest $request)
        {
            if (ArticleGroup::create($request->all())) {
                return $this->response->created();
            }

            return $this->response->errorBadRequest();
        }

        public function get($id)
        {
            $fruit = ArticleGroup::find($id);
            if ($fruit) {
                return $this->response->item($fruit, new ArticleGroupsTransformer());
            }

            return $this->response->errorNotFound();
        }

    }
```
## 009 Programmierung: API

Heute habe ich mich mit der User-Authentifizierung beschäftigt. Mein Ziel ist es den User über JSON Web Tokens mit der Api kommunizieren zu lassen. Nach dem Login wird für den User ein JSON Web Token erzeugt. Diesen schickt er bei jeder Anfrage an die Api mit. Diese kann dann überprüfen, ob der Token noch gültig ist und um welchen User es sich handelt.

```php
        /**
         *  API Login, on success return JWT Auth token
         *
         * @param \Illuminate\Http\Request $request
         *
         * @return \Illuminate\Http\JsonResponse
         */
        public function authenticate(Request $request)
        {
            // grab credentials from the request
            $credentials = array("email" => $request->json("email"), "password" => $request->json("password"));


            try {
                // attempt to verify the credentials and create a token for the user
                if (!$token = JWTAuth::attempt($credentials)) {
                    return response()->json(['error' => 'invalid_credentials'], 401);
                }
            } catch (JWTException $e) {
                // something went wrong whilst attempting to encode the token
                return response()->json(['error' => 'could_not_create_token'], 500);
            }

            // all good so return the token
            return response()->json(compact('token'));
        }
```
## 008 Programmierung: API

Heute habe ich die ersten Funktionen der Schnittstelle programmiert, die mir später die Daten an das Frontend liefert.
Hier ein paar Eindrücke.

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

## 007 Umsetzung: Navigationsleiste

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day7.png)

## 006 Design: Artikeldetail

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day6.png)

## 005 Design: Artikelübersicht

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day5.png)

## 004 Datenbankschema: Rechnungen Teil 2

Das Datenbankschema ist vorerst fertig. Als nächstes geht es an die Erstellung der einzelnen Views.

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day4.png)

## 003 Datenbankschema: Rechnungen Teil 1

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day3.png)

## 002 Datenbankschema: Kundentabelle

Heute habe ich mich mit dem Anlegen der Kundentabelle, sowie andere zugehörige Tabellen, wie zum Beispiel zugehörige Adressen.

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day2.png)

## 001 Datenbankschema: Artikel

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day1.png)
