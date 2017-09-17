# ERP in 100 Tagen

## 049 Templates: Desktop Artikeldetail Preise

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day49.png)

## 048 Templates: Tablet Artikeldetail Preise

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day48.png)

## 047 Templates: Mobile Artikeldetail Preise

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day47.png)

## 046 Templates: Desktop Artikeldetail

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day46.png)

## 045 Templates: Tablet (Quer) Artikeldetail

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day45.png)

## 044 Templates: Mobile Artikeldetail
(Leider wollte mein Chrome nicht so wie ich wollte...)

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day44.png)

## 043 Templates: Desktop Dashboard

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day43.png)

## 042 Templates: Tablet Dashboard

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day42.png)

## 041 Templates: Mobile Dashboard

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day41.png)

## 040 Templates: Mobile Menu

![alt text](https://raw.githubusercontent.com/sebi007/100days/master/day40.png)

## 039 CSS Layout Grid

```sass
$num-cols: 12;

html {
  font-size: 2vw;
}

.container {
  margin: 0 auto;
  max-width: 1280px;
  width: 90%;
}

.row {
  margin-bottom: 20px;

  &:after {
    content: "";
    display: block;
    clear: both;
  }

  .col {
    float: left;
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;

    $i: 1;
    @while($i <= $num-cols) {
      &.s#{$i} {
        width: percentage($i / $num-cols);
      }
      $i: $i + 1;
    }

    @media only screen and (min-width: 38em) {
      $i: 1;
      @while($i <= $num-cols) {
        &.m#{$i} {
          width: percentage($i / $num-cols);
        }
        $i: $i + 1;
      }
    }

    @media only screen and (min-width: 60em) {
      $i: 1;
      @while($i <= $num-cols) {
        &.l#{$i} {
          width: percentage($i / $num-cols);
        }
        $i: $i + 1;
      }
    }
  }
}
```

## 038 CSS Layout Grid

```sass
.col {
    float: left;
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;

    $i: 1;
    @while($i <= $num-cols) {
      &.s#{$i} {
        width: percentage($i / $num-cols);
      }
      $i: $i + 1;
    }

    @media only screen and (min-width: 38em) {
      $i: 1;
      @while($i <= $num-cols) {
        &.m#{$i} {
          width: percentage($i / $num-cols);
        }
        $i: $i + 1;
      }
    }
  }
```

## 037 CSS Layout Grid

```css
.row .col.s1 {
    width: 8.33333%;
}

.row .col.s2 {
    width: 16.66667%;
}

.row .col.s3 {
    width: 25%;
}

.row .col.s4 {
    width: 33.33333%;
}

.row .col.s5 {
    width: 41.66667%;
}

.row .col.s6 {
    width: 50%;
}

.row .col.s7 {
    width: 58.33333%;
}

.row .col.s8 {
    width: 66.66667%;
}

.row .col.s9 {
    width: 75%;
}

.row .col.s10 {
    width: 83.33333%;
}

.row .col.s11 {
    width: 91.66667%;
}

.row .col.s12 {
    width: 100%;
}
```

```sass
.col {
    float: left;
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;

    $i: 1;
    @while($i <= $num-cols) {
      &.s#{$i} {
        width: percentage($i / $num-cols);
      }
      $i: $i + 1;
    }
  }
```

## 036 CSS Layout Grid

```css
.container {
    margin: 0 auto;
    max-width: 1280px;
    width: 90%;
}

.row {
    margin-bottom: 20px;
}

.row:after {
    content: "";
    display: block;
    clear: both;
}

.row .col {
    float: left;
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
}

.row .col.s1 {
    width: 8.3333333333%;
    left: auto;
    right: auto;
}
```

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
