# Moje notatki
**Category**: web \
**Points**: 200

## Description
Proste, wygodne i bezpieczne rozwiązanie dla Twoich notatek!

## Solution
In this challenge we are provided a note-taking website. We can create a note by adding its title and content. Whole thing gets processed by /api/dodaj.php. In order to show notes, the website makes call to /api/pobierz.php and to show contents it goes to /api/wyswietl.php?file='mynote'. It looks like we can try to show flag by abusing the api. First, I tried some basic LFI payloads on wyswietl.php, like
```
../../../../../../etc/passwd
..\..\..\..\etc\passwd
{url encoded}
```

but without any luck. Api strips everything in the url before a slash (/) so I had to find another way. I only managed to get error with the path of the folder (/opt/app/baza_notatek). On the main site there is a parameter page that includes site glowna. Typing /glowna.php returns the same website. So the page parameter adds .php to the end. I had an idea to include my note by typing /opt/app/baza_notatek/mynote%00 but it didn't return anything. I then created a note called mynote.php with some content and successfuly managed to display it by LFI. Last step was to just create a payload which was 
```php
<?php echo system('cat /opt/app/flaga.txt') ?>.
```

## FLAG
flag{trzeba_bylo_zostac_przy_notatniku}