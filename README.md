# Laravel-Countries-DE

Laravel-Countries-DE ist ein Paket für Laravel, das ISO 3166_2, 3166_3, Währung, Hauptstadt und weitere Infos für alle Länder in deutscher Sprache enthält. Es ist ein Fork von [webpatser/laravel-countries](https://github.com/webpatser/laravel-countries).

**Laravel-Countries-DE setzt Laravel 5 voraus.**

## Installation

Füge `pille1842/laravel-countries-de` zur `composer.json` hinzu.

    "pille1842/laravel-countries-de": "dev-master"
    
Führe `composer update` aus, um die neueste Version der Länderliste herunterzuladen.

Bearbeite `app/config/app.php` und füge den `provider` und den `filter` hinzu.

    'providers' => [
        'Pille1842\Countries\CountriesServiceProvider',
    ]

Füge nun den Alias hinzu.

    'aliases' => [
        'Countries' => 'Pille1842\Countries\CountriesFacade',
    ]
    

## Model

Du kannst damit anfangen, die Konfigurationsdatei zu veröffentlichen. Dies ist ein optionaler Schritt, die Datei enthält den Tabellennamen und muss nicht zwingend verändert werden. Wenn der voreingestellte Name `countries` dir passt, lass ihn so. Führe ansonsten den folgenden Befehl aus:

    $ php artisan vendor:publish

Generiere dann die Datenbankmigration:

    $ php artisan countries:migration
    
Dadurch wird die Migration `<timestamp>_setup_countries_table.php` und der `CountriesSeeder.php` generiert. Um sicherzustellen, dass der Seeder auch ausgeführt wird, füge Folgendes zur `seeds/DatabaseSeeder.php` hinzu:

    //Seede die Länder
    $this->call('CountriesSeeder');
    $this->command->info('Seeded the countries!'); 

Du kannst ihn nun mit dem Migrate- & Seed-Kommando aufrufen:

    $ php artisan migrate --seed
    
Nach der Ausführung dieses Befehls steht die gefüllte Länderliste zur Verfügung.
